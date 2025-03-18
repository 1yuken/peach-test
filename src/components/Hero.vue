<!-- eslint-disable vue/multi-word-component-names -->
<script setup></script>

<template>
  <div class="container">
    <h2 class="hero__title">Softline</h2>
    <p class="hero__subtitle">
      Ведущий поставщик IT-решений и сервисов.* Мы предлагаем комплексные IT-решения, облака,
      программное и аппаратное обеспечение, решения по цифровой трансформации и кибербезопасности, а
      также широкий спектр IT-услуг.
    </p>
    <div class="stats">
      <div class="stats__item">
        <span class="stats__value">> 30 лет</span>
        <span class="stats__description">на IT-рынке</span>
      </div>
      <div class="stats__item">
        <span class="stats__value">4600</span>
        <span class="stats__description">сотрудников в России</span>
      </div>
      <div class="stats__item">
        <span class="stats__value">25</span>
        <span class="stats__description">городов России</span>
      </div>
      <div class="stats__item">
        <span class="stats__value">2000 +</span>
        <span class="stats__description">разработчиков</span>
      </div>
      <div class="stats__item">
        <span class="stats__value">3000 +</span>
        <span class="stats__description">сотрудников ежегодно проходят оценку и обучение</span>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.hero__title {
  margin-top: 80px;
  font-weight: 700;
  font-size: 56px;
  line-height: 120%;
  text-align: center;
  color: #b01736;
}

.hero__subtitle {
  max-width: 1110px;
  font-size: 32px;
  line-height: 120%;
  text-align: center;
  margin: 30px auto 0;
}

.stats {
  display: none;
}

.stats__item {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.stats__value {
  font-weight: 600;
  font-size: 48px;
  color: #a30c33;
}

.stats__description {
  font-size: 18px;
  line-height: 150%;
  text-align: center;
}

@media (max-width: 768px) {
  .hero__title {
    margin-top: 40px;
  }

  .hero__subtitle {
    font-size: 28px;
    margin: 15px auto 0;
  }
}

@media (max-width: 480px) {
  .hero__title {
    text-align: left;
    font-size: 40px;
  }

  .hero__subtitle {
    text-align: left;
    font-size: 24px;
  }
  .stats {
    margin-top: 40px;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
    row-gap: 10px;
  }

  .stats__item {
    width: 50%;
  }
  .stats__item:last-child {
    width: 70%;
  }
}

@media (max-width: 390px) {
    .stats__value {
        font-size: 40px;
    }

    .stats__description {
        font-size: 16px;
    }
}
</style>
