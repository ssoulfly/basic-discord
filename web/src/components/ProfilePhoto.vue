<script setup>
import { defineProps, ref, watch, defineEmits } from "vue";
import Status from "./Status.vue";
const props = defineProps(["src", "text", "type", "hovered", "noticeCount"]);
// const emit = defineEmits(["input"]);
// const value = ref(props.modelValue);

// watch(value, (newVal) => emit("input", newVal));
// watch(props, (newVal) => {
//   if (newVal.modelValue !== value.value) {
//     value.value = newVal.modelValue;
//   }
// });
</script>

<template>
  <div
    id="discord-profile-photo"
    :class="{
      hovered: type == 'server',
      user: type == 'user',
      server: type == 'server',
    }">
    <Status
      v-if="type == 'user' || noticeCount > 0"
      :notice-count="noticeCount"
      :status="'notice'" />
    <img class="discord-profile-image" :src="src" alt="" v-if="src" />
    <div class="discord-profile-text" v-else-if="type == 'server'">
      {{ text }}
    </div>
    <img
      v-else-if="type == 'user'"
      class="discord-profile-image"
      src="/logo.png" />
  </div>
</template>

<style lang="scss" scoped>
#discord-profile-photo {
  max-width: 48px;
  max-height: 48px;
  width: 48px;
  height: 48px;
  border-radius: 48px;
  transition: all 0.2s;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  background-color: #313338;
  user-select: none;
  position: relative;
  .discord-profile-image {
    border-radius: 48px;
  }
  .discord-profile-text {
    font-weight: 500;
    line-height: 1.2em;
    white-space: nowrap;
    text-transform: uppercase;
  }
  &.hovered {
    &:hover {
      background-color: #5864f2;
      border-radius: 15px;
    }
    .discord-profile-image {
      &:hover {
        background-color: #5864f2;
        border-radius: 15px;
      }
    }
  }
  img {
    width: 48px;
    height: 48px;
  }
}
</style>
