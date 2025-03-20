<script>
document.addEventListener('DOMContentLoaded', function () {
  const images = [
    '../../public/img/slider/1.png',
    '../../public/img/slider/2.png',
    '../../public/img/slider/3.png',
    '../../public/img/slider/4.png',
    '../../public/img/slider/5.png',
  ]

  let currentIndex = 0
  const sliderImg = document.querySelector('.corporate__slider-img')
  const prevBtn = document.querySelector('.corporate__btns .corporate__btn:first-child')
  const nextBtn = document.querySelector('.corporate__btns .corporate__btn:last-child')
  const pagination = document.querySelector('.corporate__pagination')

  function updateSlider(index) {
    sliderImg.src = images[index]
    document.querySelectorAll('.corporate__line').forEach((line, i) => {
      line.classList.toggle('active', i === index)
    })
  }

  prevBtn.addEventListener('click', function () {
    currentIndex = (currentIndex - 1 + images.length) % images.length
    updateSlider(currentIndex)
  })

  nextBtn.addEventListener('click', function () {
    currentIndex = (currentIndex + 1) % images.length
    updateSlider(currentIndex)
  })

  images.forEach((_, index) => {
    const line = document.createElement('div')
    line.classList.add('corporate__line')
    line.style.width = 100 / images.length + '%'
    if (index === 0) line.classList.add('active')
    line.addEventListener('click', function () {
      currentIndex = index
      updateSlider(currentIndex)
    })
    pagination.appendChild(line)
  })

  if (window.innerWidth <= 768) {
    let touchStartX = 0
    let touchEndX = 0
    const threshold = 50

    sliderImg.addEventListener('touchstart', function (event) {
      touchStartX = event.changedTouches[0].screenX
    })

    sliderImg.addEventListener('touchend', function (event) {
      touchEndX = event.changedTouches[0].screenX
      handleGesture()
    })

    function handleGesture() {
      if (touchEndX < touchStartX - threshold) {
        currentIndex = (currentIndex + 1) % images.length
        updateSlider(currentIndex)
      }
      if (touchEndX > touchStartX + threshold) {
        currentIndex = (currentIndex - 1 + images.length) % images.length
        updateSlider(currentIndex)
      }
    }
  }
})
</script>

<template>
  <div class="container">
    <div class="corporate">
      <div class="corporate__content">
        <h2 class="corporate__title">Корпоративная жизнь</h2>
        <div class="corporate__btns">
          <button class="corporate__btn">
            <img src="/public/img/arrow-left.svg" alt="slide left" />
          </button>
          <button class="corporate__btn">
            <img src="/public/img/arrow-right.svg" alt="slide right" />
          </button>
        </div>
      </div>
      <img class="corporate__slider-img" src="../../public/img/slider/1.png" alt="photo" />
      <div class="corporate__pagination"></div>
    </div>
  </div>
</template>

<style lang="scss">
.corporate {
  margin-top: 100px;
  padding-bottom: 55px;
}
.corporate__content {
  margin-bottom: 55px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.corporate__title {
  font-weight: 600;
  font-size: 56px;
  line-height: 100%;
  text-align: center;
}
.corporate__btns {
  display: flex;
  gap: 20px;
}
.corporate__btn {
  padding: 20px;
  background: rgba(0, 0, 0, 0.05);
  border-radius: 50%;
  width: 56px;
  height: 56px;
  display: flex;
  justify-content: center;
  align-items: center;
  outline: none;
  transition: all 0.3s ease-in-out;
  &:hover {
    background: rgba(0, 0, 0, 0.1);
  }
}
.corporate__slider-img {
  width: 100%;
  display: block;
}
.corporate__pagination {
  display: flex;
  margin-top: 20px;
  width: 100%;
  gap: 10px;
}
.corporate__line {
  height: 4px;
  background: rgba(0, 0, 0, 0.1);
  cursor: pointer;
  transition: all 0.3s ease-in-out;
}
.corporate__line.active {
  opacity: 1;
  background: #a30c33;
  transform: scaleY(1.5);
}

@media (max-width: 768px) {
  .corporate__btns {
    display: none;
  }
}
@media (max-width: 480px) {
.corporate {
  margin-top: 50px;
}
  .corporate__title {
    font-size: 36px;
  }
  .corporate__pagination {
    display: none;
  }
  .corporate__content {
    margin-bottom: 15px;
  }
}
@media (max-width: 390px) {
  .corporate__title {
    font-size: 28px;
  }
}
</style>
