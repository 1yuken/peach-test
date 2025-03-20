<!-- eslint-disable vue/multi-word-component-names -->
<script setup></script>

<template>
  <div class="container">
    <div class="mission">
      <img class="mission__bg-img" src="/public/img/bg.png" alt="" />
      <h3 class="mission__title">Миссия Softline</h3>
      <p class="mission__description">
        Мы помогаем организациям трансформироваться, работать эффективно и безопасно в условиях
        цифровой экономики.
      </p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.mission__bg-img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -1;
}

.mission {
  margin-top: 100px;
  background-color: #cb0f41;
  padding: 140px 70px 140px;
  position: relative;
  z-index: 0;

  &::before {
    position: absolute;
    content: '';
    top: 50%;
    left: 0;
    transform: translateY(-50%);
    width: 350px;
    height: 350px;
    background-image: url('/public/img/left-pattern.svg');
    background-repeat: no-repeat;
    background-size: contain;
    z-index: -1;
  }

  &::after {
    position: absolute;
    content: '';
    top: 50%;
    right: 0;
    transform: translateY(-50%);
    width: 350px;
    height: 350px;
    background-image: url('/public/img/right-pattern.svg');
    background-repeat: no-repeat;
    background-position: right center;
    background-size: contain;
    z-index: -1;
  }
}

.mission__title {
  font-size: 56px;
  font-weight: 600;
  color: #fff;
  text-align: center;
}

.mission__description {
  margin-top: 40px;
  max-width: 1110px;
  font-size: 32px;
  color: #fff;
  text-align: center;
}

@media (max-width: 1024px) {
  .mission {
    padding: 120px 50px 120px;

    &::before,
    &::after {
      width: 300px;
      height: 300px;
    }
  }
}

@media (max-width: 768px) {
  .mission {
    padding: 100px 50px 100px;

    &::before,
    &::after {
      width: 300px;
      height: 300px;
    }
  }

  .mission__title {
    font-size: 40px;
  }

  .mission__description {
    margin-top: 20px;
    font-size: 28px;
  }
}

@media (max-width: 480px) {
  .mission {
    padding: 50px 20px 50px;
    margin-top: 50px;

    &::before,
    &::after {
      width: 200px;
      height: 200px;
    }
  }

  .mission__title {
    font-size: 32px;
  }

  .mission__description {
    margin-top: 20px;
    font-size: 22px;
  }
}

@media (max-width: 390px) {
  .mission__title {
    font-size: 28px;
  }

  .mission__description {
    margin-top: 10px;
    font-size: 16px;
  }
}
</style>
