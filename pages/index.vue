<template>
  <div class="wrapper">
    <HeaderMain />
    <main class="main">
      <div class="main__wrapper">
        <SectionAbout />
        <SectionBenefits />
      </div>
      <div class="main__bg">
        <div class="main__bg-item"></div>
        <div class="main__bg-item"></div>
      </div>
    </main>
  </div>
</template>

<script setup></script>

<style lang="scss">
.wrapper {
  background: $gray_800;
}
</style>
