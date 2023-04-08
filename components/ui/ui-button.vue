<template>
  <button
    :class="[
      'ui-button',
      {
        'ui-button__type-default': type === 'default',
        'ui-button__type-outline': type === 'outline',
        'ui-button__type-flat': type === 'flat',
        'ui-button__size-default': size === 'default',
        'ui-button__size-medium': size === 'medium',
        'ui-button__background-green': background === 'green',
        'ui-button__background-green-light': background === 'green-light',
        'ui-button__background-orange': background === 'orange',
        'ui-button__background-white': background === 'white',
        'ui-button__background-black': background === 'black',
        'ui-button__icon-only': !isText && (prefix || suffix),
        'ui-button__disabled': disabled,
        'ui-button__loading': loading,
      },
    ]"
    @click="click"
  >
    <span
      v-if="prefix"
      class="ui-button-icon"
      :class="prefix"
      :style="`margin-right:${isText ? 13 : 0}px;`"
    ></span>
    <span v-if="text && text.length && !$slots.text">
      {{ text }}
    </span>
    <span v-if="$slots.text || (text && text.length && $slots.text)">
      <slot name="text"></slot>
    </span>
    <span
      v-if="suffix"
      class="ui-button-icon"
      :class="suffix"
      :style="`margin-left:${isText ? 13 : 0}px;`"
    ></span>
  </button>
</template>

<script>
export default {
  name: 'UiButton',
  props: {
    text: {
      type: String,
      default: '',
    },
    background: {
      type: String,
      default: 'green',
      validator(value) {
        return ['green', 'green-light', 'orange', 'white', 'black'].includes(
          value
        );
      },
    },
    type: {
      type: String,
      default: 'default',
      validator(value) {
        return ['default', 'outline', 'flat'].includes(value);
      },
    },
    size: {
      type: String,
      default: 'default',
      validator(value) {
        return ['default', 'medium'].includes(value);
      },
    },
    prefix: {
      type: String,
      default: '',
    },
    suffix: {
      type: String,
      default: '',
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    block: {
      type: Boolean,
      default: false,
    },
    loading: {
      type: Boolean,
      default: false,
    },
    btnType: {
      type: String,
      default: 'button',
      validator(value) {
        return ['button', 'submit', 'reset'].includes(value);
      },
    },
  },
  data() {
    return {
      isHover: false,
    };
  },
  computed: {
    isText() {
      return !!(this.text && this.text.length);
    },
  },
  methods: {
    click() {
      this.$emit('click');
    },
  },
};
</script>

<style lang="scss">
.ui-button {
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: $font_title;
  position: relative;
  text-align: center;
  font-weight: 700;
  font-size: 14px;
  line-height: 16px;
  transition: 0.2s;
  cursor: pointer;
  padding: 12px 16px;
  border-radius: 90px;
  border: none;
  outline: none;
  color: $gray_800;
  background: $primary_yellow;
  &.ui-button__disabled {
    opacity: 0.5;
  }

  .ui-button-icon {
    transition: 0.2s;
  }
  &__size {
    &-default {
      height: 40px;
      &.ui-button__icon-only {
        padding: 10px;
        font-size: 19px;
        line-height: 1;
      }
    }
    &-medium {
      height: 48px;
      font-size: 16px;
      padding: 16px 24px;
      &.ui-button__icon-only {
        font-size: 19px;
        line-height: 1;
        padding: 14px;
      }
    }
  }
  &__type {
    &-default {
      &:hover,
      &.ui-button__disabled {
        background: linear-gradient(
            0deg,
            rgba(0, 0, 0, 0.25),
            rgba(0, 0, 0, 0.25)
          ),
          $primary_yellow;
      }
    }
    &-outline {
      border: 2px solid $gray_500;
      background: transparent;
      color: $gray_100;
      &:hover,
      &.ui-button__disabled {
        color: $gray_700;
        background: $gray_100;
        border: 2px solid $gray_100;
      }

      &.ui-button {
        &__size {
          &-medium {
            &.ui-button__icon-only {
              padding: 14px 12px;
            }
          }
        }
      }
      &.ui-button__icon-only {
        padding: 10px 8px;
      }
    }
    &-flat {
      background: transparent;
      color: $gray_100;
      &:hover,
      &.ui-button__disabled {
        background: $gray_700;
        .ui-button-icon {
          color: $gray_100;
        }
      }
      .ui-button-icon {
        color: $gray_600;
      }
    }
  }
}
</style>
