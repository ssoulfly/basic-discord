<script setup>
import { defineProps, ref } from "vue";

const props = defineProps(["modelValue", "label"]);
const checked = ref(false);
</script>

<template>
  <div id="discord-checkbox">
    <div class="checkbox">
      <input type="checkbox" v-model="checked" />
      <span class="checkmark"></span>
    </div>
    <div class="label">
      {{ label }}
    </div>
  </div>
</template>

<style lang="scss" scoped>
#discord-checkbox {
  display: flex;
  align-items: center;
  .label {
    font-size: 12px;
    font-family: "gg sans", "Noto Sans", "Helvetica Neue", Helvetica, Arial,
      sans-serif;
    line-height: 16px;
    color: #80848e;
    margin-top: 8px;
    font-weight: 400;
  }
  .checkbox {
    display: block;
    position: relative;
    padding-left: 35px;
    margin-bottom: 12px;
    cursor: pointer;
    font-size: 22px;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;

    input {
      position: absolute;
      opacity: 0;
      left: 0;
      top: 0;
      cursor: pointer;
      height: 23px;
      width: 23px;
      z-index: 999;
    }
    .checkmark {
      position: absolute;
      top: 0;
      left: 0;
      height: 23px;
      width: 23px;
      background-color: #eeeeee00;
      border: 1px solid #80848e;
      border-radius: 6px;
    }
    input:checked {
      ~ .checkmark {
        background: #5865f2 !important;
        display: flex;
        align-items: center;
        justify-content: center;
        &:after {
          content: "";
          width: 5px;
          height: 10px;
          top: 1px;
          border: solid white;
          border-width: 0 1.5px 1.5px 0;
          -webkit-transform: rotate(45deg);
          -ms-transform: rotate(45deg);
          transform: rotate(45deg);
          margin-bottom: 3px;
        }
      }
    }
  }
}
</style>
