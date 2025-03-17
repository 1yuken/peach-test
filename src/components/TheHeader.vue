<script setup></script>

<template>
  <div class="container">
    <div class="header">
      <a href="#"><img class="header__logo" src="/public/logo.svg" alt="logo" /></a>
      <nav class="header-nav">
        <ul class="header-nav__list">
          <li class="header-nav__item">
            <a class="header-nav__link" href="#">Облачные решения</a>
          </li>
          <li class="header-nav__item">
            <a class="header-nav__link" href="#">Кибербезопасность</a>
          </li>
          <li class="header-nav__item">
            <a class="header-nav__link" href="#">Импортозамещение</a>
          </li>
          <li class="header-nav__item">
            <a class="header-nav__link" href="#">Цифровая трансформация</a>
          </li>
        </ul>
      </nav>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  padding: 25px 70px;
  position: relative;
  border: 1px solid #d9d9d9;
}

.header-nav__list {
  display: flex;
  align-items: center;
  gap: 20px;
}

.header-nav__link {
  font-size: 18px;
  font-weight: 600;
  transition: color 0.4s ease-in-out;

  &:hover {
    color: #b01736;
  }
}
</style>
