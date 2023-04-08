<template>
  <div class="modal" v-if="show">
    <div class="modal__overlay" @click="closePopup"></div>
    <div class="modal__content">
      <slot></slot>
      <ui-button
        type="flat"
        class="modal__close"
        prefix="icon-close"
        @click="closePopup"
      >
      </ui-button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    show: {
      type: Boolean,
      default: false,
    },
    id: {
      type: String,
      required: true,
    },
  },
  methods: {
    closePopup() {
      this.$emit('close', this.id);
    },
  },
};
</script>

<style lang="scss">
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  @media screen and (max-width: 767px) {
    align-items: flex-end;
    justify-content: flex-start;
  }
  &__overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba($gray_600, 0.9);
  }

  &__content {
    position: relative;
    display: flex;
    justify-content: center;
    border-radius: 25px;
    overflow: hidden;
    @media screen and (max-width: 767px) {
      margin: 10px;
      width: 100%;
    }
  }

  &__info {
    position: relative;
    overflow: hidden;
    width: 385px;
    background: $primary_green;
    color: $gray_100;
    padding: 65px 53px;
    @media screen and (max-width: 767px) {
      display: none;
    }

    &::before {
      content: '';
      pointer-events: none;
      user-select: none;
      position: absolute;
      top: -14px;
      left: -3px;
      width: 900px;
      height: 182px;
      display: block;
      background: url('@/assets/images/graph_white.svg');
      z-index: 0;
    }

    &::after {
      content: '';
      pointer-events: none;
      user-select: none;
      position: absolute;
      bottom: 0;
      left: -65px;
      width: 900px;
      height: 161px;
      display: block;
      background: url('@/assets/images/Lines.svg');
      z-index: 0;
    }

    &-content {
      position: relative;
      z-index: 1;
    }

    &-title {
      font-family: $font_title;
      font-size: 25px;
      line-height: 40px;
      margin-bottom: 65px;
    }
  }

  &__form {
    display: flex;
    flex-direction: column;
    gap: 10px;
    align-items: center;
  }

  &__social {
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 10px;
    padding: 15px 0;
    text-align: center;
    &-title {
      font-weight: 700;
      font-size: 12px;
      line-height: 12px;
      text-transform: uppercase;
    }

    &-row {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    &-icon {
      flex: 0 0 45px;
      height: 45px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 25px;
      transition: 0.2s;
      border: 1px solid transparent;
      &.active {
        background: $gray_600;
        border-color: $gray_600;
      }
    }

    &-input {
      flex: 0 1 100%;
    }
  }

  &__data {
    display: flex;
    flex-direction: column;
    gap: 25px;
    width: 355px;
    background-color: rgba($gray_800, 0.9);
    padding: 25px 30px;
    z-index: 1;
    @media screen and (max-width: 767px) {
      width: 100%;
    }
  }

  &__heading {
    display: flex;
    align-items: center;
    gap: 10px;
  }

  &__icon {
    display: flex;
    align-items: center;
    justify-content: center;
    flex: 0 0 45px;
    height: 45px;
    font-size: 25px;
    line-height: 1;
    color: $gray_100;
    border-radius: 15px;
    background: $primary_orange;
    &_reg {
      background: $primary_green;
    }
  }

  &__close {
    position: absolute;
    top: 10px;
    right: 10px;
    z-index: 1;
  }
}
</style>
