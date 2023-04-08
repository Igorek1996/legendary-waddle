<template>
  <section class="section benefits">
    <div class="container">
      <div class="benefits__container">
        <h2 class="h4 benefits__title">Тим, хто нагоняє Траф</h2>

        <div class="benefits__row">
          <div class="benefits__item">
            <div class="benefits__item-img">
              <div class="benefits__item-icon">
                <span class="icon-megaphone"></span>
              </div>
            </div>
            <div class="benefits__item-text">
              <p class="text-bold">
                Круті акції, призи та прибуткова <br />
                бонусна програма
              </p>
              <p>
                Ми постійно працюємо над тим, щоб вам було цікаво та вигідно!
              </p>
            </div>
          </div>
          <div class="benefits__item">
            <div class="benefits__item-img">
              <div class="benefits__item-icon">
                <span class="icon-smile"></span>
              </div>
            </div>
            <div class="benefits__item-text">
              <p class="text-bold">
                Особлива підтримка <br />
                для кожного 24/7
              </p>
              <p>У вас буде свій персональний менеджер</p>
            </div>
          </div>
          <div class="benefits__item">
            <div class="benefits__item-img">
              <div class="benefits__item-icon">
                <span class="icon-chartbar"></span>
              </div>
            </div>
            <div class="benefits__item-text">
              <p class="text-bold">
                Детальна <br />
                статистика
              </p>
              <p>
                Миттєве оновлення, зрозуміла система відображення статистики
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {};
</script>

<style lang="scss">
.benefits {
  @media screen and (max-width: 767px) {
    order: -1;
  }
  &__title {
    text-align: center;
    margin-bottom: 75px;
    @media screen and (max-width: 767px) {
      margin-bottom: 35px;
    }
  }

  &__row {
    display: flex;
    justify-content: space-between;
    @media screen and (max-width: 767px) {
      flex-direction: column;
      justify-content: flex-start;
      gap: 25px;
    }
  }

  &__item {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    gap: 25px;
    flex: 0 1 345px;
    text-align: center;
    @media screen and (max-width: 767px) {
      flex: auto;
      flex-direction: row;
      text-align: left;
    }
    &-icon {
      display: flex;
      align-items: center;
      justify-content: center;
      flex: 0 0 65px;
      font-size: 35px;
      line-height: 1;
      color: $gray_600;
      border-radius: 15px;
      background: $primary_yellow;
      padding: 15px;
      @media screen and (max-width: 767px) {
        flex: 0 0 45px;
        padding: 10px;
      }
    }

    &-text {
      flex: 0 1 100%;
      display: flex;
      flex-direction: column;
      gap: 25px;
      @media screen and (max-width: 767px) {
        gap: 5px;
      }
    }
  }
}
</style>
