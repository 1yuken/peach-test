<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="container">
    <div class="additions">
      <div>
        <h2 class="additions__title">Компенсационный пакет</h2>
        <div class="additions__blocks">
          <div class="additions__block">
            <div class="additions__block-img">
              <img src="/public/img/additions/1.svg" alt="#" />
            </div>
            <span class="additions__block-title">ДМС</span>
          </div>
          <div class="additions__block">
            <div class="additions__block-img">
              <img src="/public/img/additions/2.svg" alt="#" />
            </div>
            <span class="additions__block-title">Выходной в день рождения</span>
          </div>
          <div class="additions__block">
            <div class="additions__block-img">
              <img src="/public/img/additions/3.svg" alt="#" />
            </div>
            <span class="additions__block-title">Корпоративная мобильная связь</span>
          </div>
          <div class="additions__block">
            <div class="additions__block-img">
              <img src="/public/img/additions/4.svg" alt="#" />
            </div>
            <span class="additions__block-title">Корпоративные скидки на спорт</span>
          </div>
          <div class="additions__block">
            <div class="additions__block-img">
              <img src="/public/img/additions/6.svg" alt="#" />
            </div>
            <span class="additions__block-title">LTI</span>
          </div>
        </div>
      </div>

      <div class="additions__divider"></div>

      <div>
        <h2 class="additions__title">
          Программа дополнительной мотивации <br />
          <span>доплата 12% от суммы</span>
        </h2>
        <div class="additions__blocks">
          <div class="additions__block">
            <div class="additions__block-img">
              <img src="/public/img/additions/7.svg" alt="#" />
            </div>
            <span class="additions__block-title">Оргхтехники</span>
          </div>
          <div class="additions__block">
            <div class="additions__block-img">
              <img src="/public/img/additions/1.svg" alt="#" />
            </div>
            <span class="additions__block-title">ДМС</span>
          </div>
          <div class="additions__block">
            <div class="additions__block-img">
              <img src="/public/img/additions/8.svg" alt="#" />
            </div>
            <span class="additions__block-title">Ипотеки</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.additions {
  margin-top: 100px;
  box-shadow: 0px 0px 40px 0px rgba(0, 0, 0, 0.06);
  padding: 80px 110px;
  display: flex;
  flex-direction: column;
  gap: 72.5px;
}
.additions__title {
  margin-bottom: 50px;
  font-size: 56px;
  text-align: center;
  font-weight: 600;

  span {
    color: #b01736;
  }
}
.additions__blocks {
  display: flex;
  justify-content: center;
  gap: 16px;
}

.additions__block {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: auto 34px;
  max-width: 178px;
  width: 100%;
}

.additions__block-img {
  margin: 0 auto;
  padding: 20px;
  background: rgba(0, 0, 0, 0.05);
  border-radius: 50%;
  width: 110px;
  height: 110px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.additions__block-img img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}

.additions__block-title {
  margin-top: 10px;
  max-width: 178px;
  font-size: 18px;
  text-align: center;
}

.additions__divider {
  width: 100%;
  height: 1px;
  background-color: #e0e0e0;
  margin: 40px 0;
}

@media (max-width: 992px) {
  .additions__blocks {
    flex-wrap: wrap;
  }
}

@media (max-width: 768px) {
  .additions {
    margin-top: 50px;
    padding: 30px 30px;
    gap: 31px;
  }
}

@media (max-width: 480px) {
  .additions__title {
    font-size: 36px;
  }

  .additions__block-img {
    padding: 10px;
    width: 90px;
    height: 90px;
  }
  .additions__block {
    max-width: 140px;
  }
}

@media (max-width: 390px) {
  .additions__title {
    font-size: 28px;
  }

  .additions__block-img {
    padding: 5px;
    width: 70px;
    height: 70px;

    img {
      transform: scale(0.8);
    }
  }
  .additions__block {
    max-width: 100px;
  }
  .additions__block-title {
    font-size: 16px;
  }
  .additions__divider {
    margin: 20px 0;
  }
}
</style>
