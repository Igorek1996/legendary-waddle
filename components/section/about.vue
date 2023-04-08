<template>
  <section class="section about">
    <div class="container">
      <div class="about__container">
        <h1 class="h3 about__title">Володарі Трафіку</h1>
        <p>
          SC Partners – нова партнерська мережа з величезним досвідом та
          експертизою. Кожен наш партнер отримує очікувану вигоду на абсолютно
          прозорих умовах та бездоганний супровід. Ми будемо поряд з вами: на
          відстані одного повідомлення в месенджері або дзвінка, адже ми
          працюємо поряд з вами.
        </p>
        <div class="about__stars">
          <span class="icon-star"></span>
          <span class="icon-star"></span>
          <span class="icon-star"></span>
          <span class="icon-star"></span>
          <span class="icon-star"></span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {};
</script>

<style lang="scss">
.about {
  text-align: center;
  &__container {
    display: flex;
    flex-direction: column;
    gap: 25px;
    width: 900px;
    max-width: 100%;
    margin: 0 auto;
    padding: 39px 44px;
    background: rgb($gray_700, 0.5) url('@/assets/images/graph.svg') center
      center no-repeat;
    border-radius: 24px;

    @media screen and (max-width: 767px) {
      padding: 25px;
    }
  }

  &__title {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 25px;
    @media screen and (max-width: 767px) {
      gap: 10px;
    }
    &::after,
    &::before {
      content: '';
      display: inline-block;
      width: 36px;
      height: 45px;
      background-image: url('@/assets/images/horns.png');
      background-size: contain;
      @media screen and (max-width: 767px) {
        width: 20px;
        height: 25px;
      }
    }

    &::after {
      transform: scale(-1, 1);
    }
  }

  &__stars {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 26px;
    font-size: 15px;
    line-height: 1;
    color: $gray_600;
  }
}
</style>
