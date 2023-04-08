<template>
  <div class="ui-page-input">
    <h1 class="text-h1">Input v2 (numbers only)</h1>
    <h3 class="text-h3">Default</h3>
    <ui-input v-model="model" label="Label" placeholder="Input caption" />
    <h3 class="text-h3">Suffix</h3>
    <ui-input
      v-model="model"
      label="Label"
      placeholder="Оберіть варіант"
      suffix="₴"
    />
    <h3 class="text-h3">Error</h3>
    <ui-input
      v-model="model"
      label="Label"
      placeholder="Оберіть варіант"
      suffix="icon-reset"
      error="Display error message here."
    />
    <h3 class="text-h3">Success</h3>
    <ui-input
      v-model="model"
      label="Label"
      success
      suffix="icon-check"
      placeholder="Оберіть варіант"
    />
    <h3 class="text-h3">Disabled</h3>
    <ui-input
      v-model="model"
      label="Label"
      placeholder="Оберіть варіант"
      suffix="₴"
      disabled
    />
    <h3 class="text-h3">Password</h3>
    <ui-input
      type="password"
      v-model="model"
      label="Label"
      placeholder="Оберіть варіант"
      suffix="icon-eye"
    />
  </div>
</template>

<script>
export default {
  name: 'UiPageInput',
  data() {
    return {
      model: '',
    };
  },
};
</script>

<style lang="scss">
.ui-page-input {
  background: black;
}
</style>
