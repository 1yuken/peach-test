<script>
document.addEventListener('DOMContentLoaded', () => {
  const navItems = document.querySelectorAll('.map__nav-item')
  const mapImg = document.querySelector('.map__img')

  navItems.forEach((item) => {
    item.addEventListener('click', () => {
      navItems.forEach((i) => i.classList.remove('active'))
      item.classList.add('active')
      const mapName = item.getAttribute('data-map')
      mapImg.src = `./img/map/${mapName}.svg`
    })
  })

  const officesBtn = document.querySelector('.map__nav-btn')
  const mapNav = document.querySelector('.map__nav')

  const overlay = document.createElement('div')
  overlay.className = 'modal-overlay'
  overlay.style.display = 'none'
  document.body.appendChild(overlay)

  const modal = document.createElement('div')
  modal.className = 'offices-modal'
  modal.style.display = 'none'

  modal.innerHTML = `
    <div class="offices-modal__content">
      <div class="offices-modal__body">
        <div class="offices-modal__cities">
          <div class="offices-modal__region">
            <h4>Москва</h4>
          </div>
          <div class="offices-modal__region">
            <h4>Центр</h4>
            <ul>
              <li>Воронеж</li>
              <li>Ярославль</li>
              <li>Белгород</li>
            </ul>
          </div>
          <div class="offices-modal__region">
            <h4>Северо-Запад</h4>
            <ul>
              <li>Санкт-Петербург</li>
              <li>Калининград</li>
            </ul>
          </div>
          <div class="offices-modal__region">
            <h4>Юг</h4>
            <ul>
              <li>Ростов-на-Дону</li>
              <li>Краснодар</li>
              <li>Волгоград</li>
            </ul>
          </div>
          <div class="offices-modal__region">
            <h4>Волга</h4>
            <ul>
              <li>Казань</li>
              <li>Самара</li>
              <li>Уфа</li>
              <li>Оренбург</li>
              <li>Нижний Новгород</li>
            </ul>
          </div>
          <div class="offices-modal__region">
            <h4>Урал</h4>
            <ul>
              <li>Екатеринбург</li>
              <li>Челябинск</li>
              <li>Пермь</li>
              <li>Сургут</li>
              <li>Тюмень</li>
              <li>Ижевск</li>
            </ul>
          </div>
          <div class="offices-modal__region">
            <h4>Сибирь</h4>
            <ul>
              <li>Новосибирск</li>
              <li>Омск</li>
              <li>Томск</li>
              <li>Красноярск</li>
              <li>Иркутск</li>
            </ul>
          </div>
          <div class="offices-modal__region">
            <h4>Дальний Восток</h4>
            <ul>
              <li>Хабаровск</li>
              <li>Владивосток</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  `

  mapNav.insertAdjacentElement('afterend', modal)

  officesBtn.addEventListener('click', () => {
    const isVisible = modal.style.display === 'block'

    if (!isVisible) {
      modal.style.display = 'block'
      overlay.style.display = 'block'
      officesBtn.classList.add('active')

      officesBtn.style.position = 'relative'
      officesBtn.style.zIndex = '1001'
    } else {
      modal.style.display = 'none'
      overlay.style.display = 'none'
      officesBtn.classList.remove('active')
    }
  })

  overlay.addEventListener('click', () => {
    modal.style.display = 'none'
    overlay.style.display = 'none'
    officesBtn.classList.remove('active')
  })

  document.querySelectorAll('.offices-modal__region h4').forEach((header) => {
    header.addEventListener('click', () => {
      const list = header.nextElementSibling

      if (list && list.tagName === 'UL') {
        const isOpen = list.classList.contains('visible')

        document.querySelectorAll('.offices-modal__region ul').forEach((ul) => {
          ul.classList.remove('visible')
          ul.style.maxHeight = '0px'
        })

        document.querySelectorAll('.offices-modal__region h4').forEach((h4) => {
          h4.classList.remove('open')
        })

        if (!isOpen) {
          list.classList.add('visible')
          list.style.maxHeight = list.scrollHeight + 'px'
          header.classList.add('open')
        }
      }
    })
  })
})
</script>

<template>
  <div class="container">
    <div class="map">
      <div class="map__nav">
        <button class="map__nav-btn">Офисы Softline</button>
        <ul class="map__nav-list">
          <li class="map__nav-item active" data-map="all">Все</li>
          <li class="map__nav-item" data-map="moscow">Москва</li>
          <li class="map__nav-item" data-map="center">Центр</li>
          <li class="map__nav-item" data-map="severo-zapad">Северо-Запад</li>
          <li class="map__nav-item" data-map="yug">Юг</li>
          <li class="map__nav-item" data-map="volga">Волга</li>
          <li class="map__nav-item" data-map="ural">Урал</li>
          <li class="map__nav-item" data-map="sibir">Сибирь</li>
          <li class="map__nav-item" data-map="dalniy-vostok">Дальний восток</li>
        </ul>
      </div>
      <div class="map__img-container">
        <img class="map__img" src="/img/map/all.svg" alt="Map" />
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.container {
  max-width: 1200px;
  margin: 0 auto;
  position: relative;
}

.map {
  margin-top: 80px;
  display: flex;
  flex-direction: column;
  position: relative;
}

.map__nav {
  margin-bottom: 100px;
  display: flex;
  justify-content: space-between;
  gap: 15px;
  align-items: center;
  padding: 24px 70px;
  box-shadow: 0px 0px 40px 0px rgba(0, 0, 0, 0.06);
  position: relative;
  z-index: 1002;
}

.map__nav-btn {
  font-weight: 600;
  font-size: 24px;
  position: relative;
  cursor: pointer;
  background: none;
  border: none;
  padding: 0;
  transition: color 0.3s;
}

.map__nav-btn::after {
  position: absolute;
  content: '';
  width: 24px;
  height: 24px;
  top: 50%;
  right: -40px;
  transform: translateY(-50%);
  background-image: url('/peach-test/img/arrow-down.svg');
  background-repeat: no-repeat;
  background-position: center;
  transition: transform 0.3s;
}

.map__nav-btn.active::after {
  transform: translateY(-50%) rotate(180deg);
}

.map__nav-list {
  display: flex;
  align-items: center;
  gap: 30px;
  list-style: none;
  padding: 0;
  margin: 0;
}

.map__nav-item {
  font-size: 18px;
  font-weight: 600;
  cursor: pointer;
  position: relative;
}

.map__nav-item.active {
  color: #b01736;
}

.map__nav-item.active::after {
  position: absolute;
  content: '';
  width: 100%;
  height: 3px;
  background-color: #b01736;
  left: 50%;
  bottom: -28px;
  transform: translateX(-50%);
}

.map__img {
  max-width: 100%;
  height: auto;
  display: block;
  position: relative;
  z-index: 1;
}

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(255, 255, 255, 0.8);
  z-index: 1000;
}

.offices-modal {
  position: absolute;
  top: 100px;
  left: 0;
  right: 0;
  z-index: 1001;
  background-color: #fff;
  box-shadow: 0px 4px 20px rgba(0, 0, 0, 0.1);
  border-radius: 0 0 8px 8px;
  width: 100%;
}

.offices-modal__content {
  padding: 20px;
  display: flex;
  flex-direction: column;
}

.offices-modal__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

.offices-modal__header h3 {
  font-size: 24px;
  font-weight: 600;
  margin: 0;
}

.offices-modal__close {
  background: none;
  border: none;
  font-size: 24px;
  cursor: pointer;
  color: #999;
}

.offices-modal__tabs {
  display: flex;
  gap: 20px;
  border-bottom: 1px solid #eee;
  padding-bottom: 10px;
  margin-bottom: 20px;
  overflow-x: auto;
}

.offices-modal__tab {
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  padding: 5px 0;
  position: relative;
  white-space: nowrap;
}

.offices-modal__tab.active {
  color: #b01736;
}

.offices-modal__tab.active::after {
  position: absolute;
  content: '';
  width: 100%;
  height: 2px;
  background-color: #b01736;
  left: 0;
  bottom: -11px;
}

.offices-modal__cities {
  padding: 0 48px;
  display: flex;
  gap: 24px;
}

.offices-modal__region h4 {
  font-family: 'ProximaNova', sans-serif;
  display: inline-block;
  font-size: 18px;
  font-weight: 600;
  margin: 0 0 10px 0;
  position: relative;

  &::after {
    position: absolute;
    content: '';
    width: 8px;
    height: 5px;
    background: url('/peach-test/img/arrow-down__gray.svg');
    background-repeat: no-repeat;
    right: -15px;
    top: 50%;
    transform: translateY(10%);
    display: none;
  }
}

.offices-modal__region ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.offices-modal__region li {
  font-family: 'ProximaNova', sans-serif;
  margin-bottom: 8px;
  font-size: 16px;
}

@media (max-width: 1200px) {
  .map__nav {
    padding: 24px 20px;
  }
  .map__nav-list {
    gap: 20px;
  }
}

@media (max-width: 992px) {
  .map__nav {
    flex-direction: column;
    align-items: flex-start;
  }
  .map__nav-item.active::after {
    bottom: -24px;
  }
  .offices-modal {
    top: 130px;
  }
  .offices-modal__cities {
    flex-wrap: wrap;
  }
}

@media (max-width: 768px) {
  .offices-modal__region ul {
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.3s ease-out;
  }

  .offices-modal__region ul.visible {
    max-height: 400px;
  }

  .offices-modal__region h4 {
    cursor: pointer;
    position: relative;
    margin-right: 20px;
  }

  .offices-modal__region h4::after {
    display: block;
    transition: transform 0.3s ease;
  }

  .offices-modal__region h4.open::after {
    transform: rotate(180deg);
  }
  .offices-modal__cities {
    gap: 10px;
  }
  .map__nav-list {
    display: flex;
    flex-wrap: nowrap;
    overflow-x: auto;
    overflow-y: hidden;
    -webkit-overflow-scrolling: touch;
    gap: 10px;
    padding-bottom: 5px;
    white-space: nowrap;
    max-width: 100%;
  }

  .map__nav-item {
    flex: 0 0 auto;
    padding: 10px 15px;
  }

  .map__nav {
    overflow: hidden;
    width: 100%;
    margin-bottom: 50px;
  }

  .map__nav-list::-webkit-scrollbar {
    height: 8px;
  }

  .map__nav-list::-webkit-scrollbar-thumb {
    background: #ccc;
    border-radius: 5px;
  }
  .offices-modal {
    top: 160px;
  }
  .map__img-container {
    overflow-x: auto;
    width: 100%;
    display: flex;
  }

  .map__img {
    max-width: none;
    height: auto;
    display: block;
    flex-shrink: 0;
  }
}

@media (max-width: 480px) {
  .offices-modal__region h4 {
    font-size: 16px;
  }
  .offices-modal__region li {
    font-size: 14px;
  }
}
</style>
