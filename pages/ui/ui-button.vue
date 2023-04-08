<template>
  <div class="container ui-page-button">
    <h1>Button</h1>
    <h2>Primary</h2>
    <div class="ui-page-button__buttons">
      <ui-button text="Button" />
      <ui-button text="Button" size="medium" />
      <ui-button text="Button" prefix="icon-star" />
      <ui-button text="Button" size="medium" prefix="icon-star" />
      <ui-button text="Button" suffix="icon-star" />
      <ui-button text="Button" size="medium" suffix="icon-star" />
      <ui-button suffix="icon-star" />
      <ui-button size="medium" suffix="icon-star" />
    </div>
    <h2>Flat</h2>
    <div class="ui-page-button__buttons">
      <ui-button text="Button" type="flat" />
      <ui-button text="Button" type="flat" size="medium" />
      <ui-button text="Button" type="flat" prefix="icon-star" />
      <ui-button text="Button" type="flat" size="medium" prefix="icon-star" />
      <ui-button text="Button" type="flat" suffix="icon-star" />
      <ui-button text="Button" type="flat" size="medium" suffix="icon-star" />
      <ui-button type="flat" suffix="icon-star" />
      <ui-button type="flat" size="medium" suffix="icon-star" />
    </div>
    <h2>Outline</h2>
    <div class="ui-page-button__buttons">
      <ui-button text="Button" type="outline" />
      <ui-button text="Button" type="outline" size="medium" />
      <ui-button text="Button" type="outline" prefix="icon-star" />
      <ui-button
        text="Button"
        type="outline"
        size="medium"
        prefix="icon-star"
      />
      <ui-button text="Button" type="outline" suffix="icon-star" />
      <ui-button
        text="Button"
        type="outline"
        size="medium"
        suffix="icon-star"
      />
      <ui-button type="outline" suffix="icon-star" />
      <ui-button type="outline" size="medium" suffix="icon-star" />
    </div>
    <br /><br /><br /><br />
    <h1>Disabled</h1>
    <h2>Primary</h2>
    <div class="ui-page-button__buttons">
      <ui-button text="Button" disabled />
      <ui-button text="Button" size="medium" disabled />
      <ui-button text="Button" prefix="icon-star" disabled />
      <ui-button text="Button" size="medium" prefix="icon-star" disabled />
      <ui-button text="Button" suffix="icon-star" disabled />
      <ui-button text="Button" size="medium" suffix="icon-star" disabled />
      <ui-button suffix="icon-star" disabled />
      <ui-button size="medium" suffix="icon-star" disabled />
    </div>
    <h2>Flat</h2>
    <div class="ui-page-button__buttons">
      <ui-button text="Button" type="flat" disabled />
      <ui-button text="Button" type="flat" size="medium" disabled />
      <ui-button text="Button" type="flat" prefix="icon-star" disabled />
      <ui-button
        text="Button"
        type="flat"
        size="medium"
        prefix="icon-star"
        disabled
      />
      <ui-button text="Button" type="flat" suffix="icon-star" disabled />
      <ui-button
        text="Button"
        type="flat"
        size="medium"
        suffix="icon-star"
        disabled
      />
      <ui-button type="flat" suffix="icon-star" disabled />
      <ui-button type="flat" size="medium" suffix="icon-star" disabled />
    </div>
    <h2>Outline</h2>
    <div class="ui-page-button__buttons">
      <ui-button text="Button" type="outline" disabled />
      <ui-button text="Button" type="outline" size="medium" disabled />
      <ui-button text="Button" type="outline" prefix="icon-star" disabled />
      <ui-button
        text="Button"
        type="outline"
        size="medium"
        prefix="icon-star"
        disabled
      />
      <ui-button text="Button" type="outline" suffix="icon-star" disabled />
      <ui-button
        text="Button"
        type="outline"
        size="medium"
        suffix="icon-star"
        disabled
      />
      <ui-button type="outline" suffix="icon-star" disabled />
      <ui-button type="outline" size="medium" suffix="icon-star" disabled />
    </div>
  </div>
</template>

<script>
export default {
  name: 'UiPageButton',
  data() {
    return {};
  },
};
</script>

<style lang="scss">
.ui-page-button {
  background: black;
  padding-bottom: 100px;
  &__buttons {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
    justify-items: center;
    align-items: center;
    div {
      display: flex;
      align-items: center;
      justify-content: center;
    }
  }
}
</style>
