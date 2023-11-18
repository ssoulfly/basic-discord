<script setup>
import { defineProps } from "vue";

const props = defineProps(["text", "required"]);
</script>

<template>
  <div id="discord-label">
    {{ props.text }}<span class="required" v-if="props.required">*</span>
  </div>
</template>

<style lang="scss" scoped>
#discord-label {
  color: #b5bac1;
  margin-bottom: 8px;
  font-size: 12px;
  line-height: 16px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.02em;
  font-family: "gg sans", "Noto Sans", "Helvetica Neue", Helvetica, Arial,
    sans-serif;
}
.required {
  color: #f23f42;
  margin-left: 4px;
}
</style>
