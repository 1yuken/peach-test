<script setup>
document.addEventListener('DOMContentLoaded', () => {
  // Existing map navigation functionality
  const navItems = document.querySelectorAll('.map__nav-item')
  const mapImg = document.querySelector('.map__img')

  navItems.forEach((item) => {
    item.addEventListener('click', () => {
      navItems.forEach((i) => i.classList.remove('active'))
      item.classList.add('active')
      const mapName = item.getAttribute('data-map')
      mapImg.src = `/public/img/map/${mapName}.svg`
    })
  })

  // New modal functionality
  const officesBtn = document.querySelector('.map__nav-btn')
  const mapNav = document.querySelector('.map__nav')
  
  // Create overlay
  const overlay = document.createElement('div')
  overlay.className = 'modal-overlay'
  overlay.style.display = 'none'
  document.body.appendChild(overlay)
  
  // Create modal
  const modal = document.createElement('div')
  modal.className = 'offices-modal'
  modal.style.display = 'none'
  
  // Create modal content
  modal.innerHTML = `
    <div class="offices-modal__content">
      <div class="offices-modal__header">
        <h3>Офисы Softline</h3>
        <button class="offices-modal__close">&times;</button>
      </div>
      <div class="offices-modal__body">
        <div class="offices-modal__tabs">
          <div class="offices-modal__tab active" data-region="all">Все</div>
          <div class="offices-modal__tab" data-region="moscow">Москва</div>
          <div class="offices-modal__tab" data-region="center">Центр</div>
          <div class="offices-modal__tab" data-region="severo-zapad">Северо-Запад</div>
          <div class="offices-modal__tab" data-region="yug">Юг</div>
          <div class="offices-modal__tab" data-region="volga">Волга</div>
          <div class="offices-modal__tab" data-region="ural">Урал</div>
          <div class="offices-modal__tab" data-region="sibir">Сибирь</div>
          <div class="offices-modal__tab" data-region="dalniy-vostok">Дальний Восток</div>
        </div>
        <div class="offices-modal__cities">
          <div class="offices-modal__region">
            <h4>Москва</h4>
            <ul>
              <li>Москва</li>
            </ul>
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
  
  // Insert modal after the map__nav
  mapNav.insertAdjacentElement('afterend', modal)
  
  // Toggle modal on button click
  officesBtn.addEventListener('click', () => {
    const isVisible = modal.style.display === 'block'
    
    if (!isVisible) {
      modal.style.display = 'block'
      overlay.style.display = 'block'
      officesBtn.classList.add('active')
      
      // Make sure the button stays on top of the overlay
      officesBtn.style.position = 'relative'
      officesBtn.style.zIndex = '1001'
    } else {
      modal.style.display = 'none'
      overlay.style.display = 'none'
      officesBtn.classList.remove('active')
    }
  })
  
  // Close modal when clicking the close button
  const closeBtn = modal.querySelector('.offices-modal__close')
  closeBtn.addEventListener('click', () => {
    modal.style.display = 'none'
    overlay.style.display = 'none'
    officesBtn.classList.remove('active')
  })
  
  // Close modal when clicking on the overlay
  overlay.addEventListener('click', () => {
    modal.style.display = 'none'
    overlay.style.display = 'none'
    officesBtn.classList.remove('active')
  })
  
  // Handle tab clicks in the modal
  const modalTabs = modal.querySelectorAll('.offices-modal__tab')
  modalTabs.forEach((tab) => {
    tab.addEventListener('click', () => {
      // Update active tab
      modalTabs.forEach((t) => t.classList.remove('active'))
      tab.classList.add('active')
      
      // Get region and update map
      const region = tab.getAttribute('data-region')
      
      // Find and activate corresponding map nav item
      const correspondingNavItem = document.querySelector(`.map__nav-item[data-map="${region}"]`)
      if (correspondingNavItem) {
        correspondingNavItem.click()
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
      <img class="map__img" src="/public/img/map/all.svg" alt="Map" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
  position: relative;
}
.map {
  margin-top: 80px;
  display: flex;
  flex-direction: column;
}
.map__nav {
  margin-bottom: 100px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 24px 70px;
  box-shadow: 0px 0px 40px 0px rgba(0, 0, 0, 0.06);
  position: relative;
  z-index: 1002; /* Ensure nav is above overlay */
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
  background-image: url('/public/img/arrow-down.svg');
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
  height: 2px;
  background-color: #b01736;
  left: 50%;
  bottom: -6px;
  transform: translateX(-50%);
}
.map__img {
  max-width: 100%;
  height: auto;
  display: block;
  position: relative;
  z-index: 999; /* Below the modal */
}

/* Modal overlay */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(255, 255, 255, 0.8);
  z-index: 1000;
}

/* Modal styles */
.offices-modal {
  position: relative;
  z-index: 1001;
  background-color: #fff;
  box-shadow: 0px 4px 20px rgba(0, 0, 0, 0.1);
  border-radius: 0 0 8px 8px;
  margin-top: -100px; /* Negative margin to pull it up */
  margin-bottom: 100px; /* Keep the spacing for the map */
  width: 100%;
}

.offices-modal__content {
  padding: 20px;
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
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 30px;
}

.offices-modal__region h4 {
  font-size: 18px;
  font-weight: 600;
  margin: 0 0 10px 0;
  color: #b01736;
}

.offices-modal__region ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.offices-modal__region li {
  margin-bottom: 8px;
  font-size: 16px;
}
</style>

