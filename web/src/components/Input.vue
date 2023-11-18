<script setup>
import { defineProps, ref, watch, defineEmits } from "vue";

const props = defineProps(["modelValue", "required", "type", "bottom"]);
const emit = defineEmits(["input"]);
const value = ref(props.modelValue);

watch(value, (newVal) => emit("input", newVal));
watch(props, (newVal) => {
  if (newVal.modelValue !== value.value) {
    value.value = newVal.modelValue;
  }
});
</script>

<template>
  <div id="discord-input" :class="[props.bottom && 'margin-have']">
    <input
      v-model="value"
      class="input"
      v-if="(props.type || 'text') == 'text'"
      type="text"
      :required="props.required" />
    <input
      v-model="value"
      class="input"
      v-if="props.type == 'password'"
      type="password"
      :required="props.required" />
  </div>
</template>

<style scoped>
#discord-input {
  width: 100%;
}
#discord-input.margin-have {
  margin-bottom: 20px;
}
#discord-input .input {
  background-color: #1e1f22;
  padding: 10px;
  border: none;
  outline: none;
  color: white;
  width: calc(100% - 20px);
  font-size: 16px;
  border-radius: 3px;
}
#discord-input .label {
  color: #90949b;
  margin-bottom: 8px;
  font-size: 12px;
  line-height: 16px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.02em;
  font-family: "gg sans", "Noto Sans", "Helvetica Neue", Helvetica, Arial,
    sans-serif;
}
#discord-input .label .required {
  color: #9f393d;
  margin-left: 4px;
}
</style>
