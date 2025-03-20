<!-- eslint-disable vue/multi-word-component-names -->
<script>
document.addEventListener('DOMContentLoaded', function () {
  const blocks = document.querySelectorAll('.directions__block')

  function setupEventHandlers() {
    const isMobile = window.innerWidth <= 480

    blocks.forEach((block) => {
      const description = block.querySelector('.directions__block-description')
      const arrowBtn = block.querySelector('.directions__block-btn img')

      if (!isMobile && block.classList.contains('open')) {
        block.classList.remove('open')
        description.style.opacity = ''
        description.style.transform = ''
        block.style.height = ''
        if (arrowBtn) {
          arrowBtn.style.transform = ''
        }
      }

      block.removeEventListener('click', block.clickHandler)

      if (isMobile) {
        block.style.height = '60px'

        block.clickHandler = function () {
          if (block.classList.contains('open')) {
            block.classList.remove('open')
            description.style.opacity = '0'
            description.style.transform = 'translateY(20px)'

            const fullHeight = block.scrollHeight
            block.style.height = fullHeight + 'px'

            setTimeout(() => {
              block.style.height = '60px'

              if (arrowBtn) {
                arrowBtn.style.transform = 'rotate(0deg)'
              }
            }, 10)
          } else {
            block.classList.add('open')
            description.style.opacity = '1'
            description.style.transform = 'translateY(0)'

            block.style.height = 'auto'
            const fullHeight = block.scrollHeight

            block.style.height = '60px'

            setTimeout(() => {
              block.style.height = fullHeight + 'px'

              if (arrowBtn) {
                arrowBtn.style.transform = 'rotate(180deg)'
              }
            }, 5)
          }
        }

        block.addEventListener('click', block.clickHandler)
      } else {
        block.style.height = ''
      }
    })
  }

  setupEventHandlers()

  window.addEventListener('resize', setupEventHandlers)
})
</script>

<template>
  <div class="container">
    <h2 class="directions__title">Направления бизнеса</h2>
    <div class="directions__blocks">
      <div class="directions__block">
        <img class="directions__block-img" src="/public/img/business/1.png" alt="#" />
        <div class="directions__block-overlay">
          <div class="directions__block-header">
            <h3 class="directions__block-title">Решения Softline</h3>
            <button class="directions__block-btn">
              <img src="/public/img/arrow-down__white.svg" alt="#" />
            </button>
          </div>
          <p class="directions__block-description">
            ГК Softline предлагает клиентам собственную линейку оборудования (ПК, серверы, торговое
            оборудование и проч.), разработку программных продуктов, облачных решений, решений в
            области информационной безопасности.
          </p>
        </div>
      </div>
      <div class="directions__block">
        <img class="directions__block-img" src="/public/img/business/2.png" alt="#" />
        <div class="directions__block-overlay">
          <div class="directions__block-header">
            <h3 class="directions__block-title">Кибербезопасность</h3>
            <button class="directions__block-btn">
              <img src="/public/img/arrow-down__white.svg" alt="#" />
            </button>
          </div>
          <p class="directions__block-description">
            Softline обладает всеми необходимыми государственными лицензиями для организации
            проектов по информационной безопасности и аттестации.
          </p>
        </div>
      </div>
      <div class="directions__block">
        <img class="directions__block-img" src="/public/img/business/3.png" alt="#" />
        <div class="directions__block-overlay">
          <div class="directions__block-header">
            <h3 class="directions__block-title">Импортозамещение</h3>
            <button class="directions__block-btn">
              <img src="/public/img/arrow-down__white.svg" alt="#" />
            </button>
          </div>
          <p class="directions__block-description">
            ГК Softline обладает широчайшим портфелем решений и услуг для импортозамещения, включая
            ПО и оборудование собственного производства.
          </p>
        </div>
      </div>
      <div class="directions__block">
        <img class="directions__block-img" src="/public/img/business/4.png" alt="#" />
        <div class="directions__block-overlay">
          <div class="directions__block-header">
            <h3 class="directions__block-title">Облачные решения</h3>
            <button class="directions__block-btn">
              <img src="/public/img/arrow-down__white.svg" alt="#" />
            </button>
          </div>
          <p class="directions__block-description">
            Softline использует современные облачные решения как российских, так и международных
            вендоров для масштабирования бизнеса своих клиентов. Подписки, услуги, трансформация.
          </p>
        </div>
      </div>
      <div class="directions__block">
        <img class="directions__block-img" src="/public/img/business/5.png" alt="#" />
        <div class="directions__block-overlay">
          <div class="directions__block-header">
            <h3 class="directions__block-title">Цифровая трансформация и разработка ПО</h3>
            <button class="directions__block-btn">
              <img src="/public/img/arrow-down__white.svg" alt="#" />
            </button>
          </div>
          <p class="directions__block-description">
            Softline использует современные технологи и новые возможности для увеличения
            производительности бизнеса заказчика. В штате ГК Softline - 2000+ разработчиков, которые
            трансформируют ПО под нужды конкретного предприятия.
          </p>
        </div>
      </div>
      <div class="directions__block">
        <img class="directions__block-img" src="/public/img/business/6.png" alt="#" />
        <div class="directions__block-overlay">
          <div class="directions__block-header">
            <h3 class="directions__block-title">Техническая поддержка Softline</h3>
            <button class="directions__block-btn">
              <img src="/public/img/arrow-down__white.svg" alt="#" />
            </button>
          </div>
          <p class="directions__block-description">
            200+ инженеров, 24 часа в сутки, 7 дней в неделю, 12 месяцев в году, сервисное
            партнерство с 30+ мировыми производителями.
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.directions__title {
  margin-top: 100px;
  font-size: 56px;
  font-weight: 600;
  text-align: center;
}

.directions__blocks {
  margin-top: 55px;
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}

.directions__block {
  position: relative;
  overflow: hidden;
  width: calc(50% - 20px);
  transition: height 0.5s ease-in-out;
}

.directions__block-img {
  width: 100%;
  display: block;
}

.directions__block-overlay {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  height: 60px;
  background: rgba(45, 54, 83, 0.6);
  padding: 18px 20px;
  box-sizing: border-box;
  transition:
    height 0.3s ease-in-out,
    background 0.3s ease-in-out;
  overflow: hidden;
}

.directions__block-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.directions__block-btn {
  display: none;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 0;
}

.directions__block-btn img {
  transition: transform 0.5s ease-in-out;
}

.directions__block-title {
  font-size: 20px;
  color: #fff;
  margin: 0;
}

.directions__block-description {
  max-width: 450px;
  font-size: 16px;
  color: #fff;
  opacity: 0;
  transform: translateY(20px);
  transition:
    opacity 0.5s ease-in-out,
    transform 0.5s ease-in-out;
  margin: 20px 0 0;
}

.directions__block.open .directions__block-overlay {
  height: auto;
  background: rgba(45, 54, 83, 0.8);
}

.directions__block.open .directions__block-description {
  opacity: 1;
  transform: translateY(0);
}

.directions__block:hover .directions__block-overlay {
  height: 100%;
  background: rgba(45, 54, 83, 0.8);
}

.directions__block:hover .directions__block-description {
  opacity: 1;
  transform: translateY(0);
}

@media (max-width: 992px) {
  .directions__block-description {
    margin-top: 5px;
  }
}

@media (max-width: 884px) {
  .directions__block-title {
    font-size: 18px;
  }
}

@media (max-width: 805px) {
  .directions__block {
    width: 100%;
  }

  .directions__block-title {
    font-size: 30px;
  }

  .directions__block-description {
    max-width: 540px;
    font-size: 22px;
  }

  .directions__block-overlay {
    height: 80px;
    padding: 25px 20px;
  }
}

@media (max-width: 620px) {
  .directions__block-title {
    font-size: 26px;
  }

  .directions__block-description {
    max-width: 540px;
    font-size: 18px;
  }

  .directions__block-overlay {
    height: 80px;
    padding: 25px 20px;
  }
}

@media (max-width: 544px) {
  .directions__block-title {
    font-size: 22px;
  }

  .directions__block-description {
    max-width: 540px;
    font-size: 18px;
  }

  .directions__block-overlay {
    height: 60px;
    padding: 18px 20px;
  }
}

@media (max-width: 480px) {
  .directions__block {
    height: 60px;
    cursor: pointer;
  }
  .directions__block-btn {
    display: block;
  }
  .directions__block-title {
    font-size: 18px;
  }

  .directions__title {
    font-size: 36px;
    margin-top: 30px;
  }

  .directions__block-description {
    max-width: 540px;
    font-size: 16px;
  }
  .directions__blocks {
    margin-top: 30px;
  }
}

@media (max-width: 390px) {
  
  .directions__title {
    font-size: 28px;
  }
}
</style>
