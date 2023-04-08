<template>
  <div
    class="ui-input"
    :class="{
      'ui-input-error': error,
      'ui-input-suffix': suffix,
      'ui-input-disabled': disabled,
      'ui-input-success': success,
    }"
  >
    <label v-if="hasLabel" class="ui-input__label">
      {{ label }}
    </label>
    <div class="ui-input__input-wrap">
      <span
        v-if="suffix"
        class="ui-input__suffix"
        :class="suffix"
        :style="`margin-left:${isText ? 13 : 0}px;`"
      ></span>
      <input
        :value="value"
        class="ui-input__input"
        :type="type"
        :placeholder="placeholder"
        :autofocus="autofocus"
        :readonly="disabled"
        @change="changeValue"
        @input="updateValue"
        @blur="onBlur($event)"
        @focus="onFocus($event)"
      />
    </div>
    <transition name="error">
      <p v-if="error" class="ui-input__message">{{ error }}</p>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'UiInputV2',
  props: {
    value: {
      type: [String, Number],
      default: '',
    },
    label: {
      type: String,
      default: '',
    },
    type: {
      type: String,
      default: 'text',
    },
    placeholder: {
      type: String,
      default: '',
    },
    suffix: {
      type: String,
      default: '',
    },
    success: {
      type: Boolean,
      default: false,
    },
    error: {
      type: String,
      default: null,
    },

    autofocus: {
      type: Boolean,
      default: false,
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    hasLabel() {
      return !!(this.label && this.label.length);
    },

    isText() {
      return !!(this.text && this.text.length);
    },
  },
  methods: {
    changeValue(event) {
      this.$emit('change', event.target.value);
    },
    updateValue(event) {
      this.$emit('input', event.target.value);
    },
    onFocus(event) {
      if (!this.disabled) {
        this.$emit('focus', event);
      }
    },
    onBlur(event) {
      this.$emit('blur', event);
    },
  },
};
</script>

<style lang="scss">
.ui-input {
  position: relative;
  width: 100%;
  outline: 0;
  &__label {
    display: block;
    font-weight: 700;
    font-size: 12px;
    line-height: 1;
    color: $gray_400;
    margin-bottom: 12px;
  }
  &__input {
    width: 100%;
    height: 48px;
    padding: 16px;
    background: transparent;
    font-weight: 700;
    font-size: 14px;
    line-height: 16px;
    border: 2px solid $gray_600;
    border-radius: 70px;
    outline: 0;
    color: $gray_300;
    transition: 0.2s;
    &-wrap {
      position: relative;
    }

    &::placeholder {
      color: $gray_500;
    }
  }
  &__input:hover {
    outline: 0;
    border: 2px solid $gray_500;
  }
  &__input:focus {
    outline: 0;
    border: 2px solid $primary_yellow;
  }
  &__suffix {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    right: 12px;
    font-weight: 500;
    font-size: 24px;
    line-height: 1;
    color: gray;
  }
  &__message {
    margin-top: 5px;
    font-size: 12px;
    line-height: 12px;
    color: $primary_orange;
  }
}

.ui-input-suffix {
  .ui-input__input {
    padding-right: 30px;
  }
}
.ui-input-error {
  .ui-input__input {
    color: $primary_orange;
    border-color: currentColor;
  }
  .ui-input__suffix {
    color: $gray_500;
  }
}
.ui-input-success {
  .ui-input__input {
    border-color: $primary_green;
  }
  .ui-input__suffix {
    color: $primary_green;
  }
}
.ui-input-disabled {
  .ui-input__input {
    cursor: not-allowed;

    &:hover {
      border: 2px solid $gray_600;
    }
    &:focus {
      border: 2px solid $gray_600;
    }
  }
}

.error-enter-active,
.error-leave-active {
  transition: 0.2s;
}
.error-enter,
.error-leave-to {
  opacity: 0;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type='number'] {
  -moz-appearance: textfield;
}
</style>
