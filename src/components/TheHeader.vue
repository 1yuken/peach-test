<script setup></script>

<template>
  <div class="container">
    <header class="header">
      <a class="header__link" href="#"
        ><img class="header__logo" src="/public/logo.svg" alt="logo"
      /></a>
      <nav class="header__nav">
        <ul class="header__nav-list">
          <li class="header__nav-item">
            <a class="header__nav-link" href="#">Облачные решения</a>
          </li>
          <li class="header__nav-item">
            <a class="header__nav-link" href="#">Кибербезопасность</a>
          </li>
          <li class="header__nav-item">
            <a class="header__nav-link" href="#">Импортозамещение</a>
          </li>
          <li class="header__nav-item">
            <a class="header__nav-link" href="#">Цифровая трансформация</a>
          </li>
        </ul>
      </nav>
    </header>
  </div>
</template>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  padding: 24px 70px;
  position: relative;
  border: 1px solid #d9d9d9;
  gap: 15px;
}

.header__link {
  margin-top: 6px;
}

.header__nav-list {
  margin-top: 6px;
  display: flex;
  align-items: center;
  gap: 20px;
}

.header__nav-link {
  font-size: 18px;
  font-weight: 600;
  transition: color 0.4s ease-in-out;

  &:hover {
    color: #b01736;
  }
}

@media (max-width: 1200px) {
  .header {
    padding: 24px 50px;
  }
}

@media (max-width: 992px) {
  .header,
  .header__nav-list {
    flex-wrap: wrap;
  }
}

@media (max-width: 820px) {
  .header__nav-list {
    gap: 10px;
  }
}

@media (max-width: 480px) {
  .header {
    gap: 10px;
    padding: 24px 20px;
  }
  .header__nav-list {
    gap: 0px;
  }
  .header__nav-link {
    font-size: 16px;
    margin-right: 10px;
  }
}

@media (max-width: 390px) {
  .header {
    gap: 5px;
  }
  .header__nav-link {
    font-size: 14px;
  }
}
</style>
