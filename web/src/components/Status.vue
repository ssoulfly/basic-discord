<script setup>
import { defineProps } from "vue";

const props = defineProps(["status", "noticeCount"]);
</script>
<template>
  <div id="discord-status" v-if="noticeCount > 0" :status="status">
    {{ noticeCount }}
    <div class="border" v-if="!noticeCount" />
  </div>
</template>

<style lang="scss" scoped>
#discord-status {
  display: flex;
  align-items: center;
  justify-content: center;
  right: 1px;
  width: 12px;
  height: 12px;
  background-color: #2b2d31;
  border-radius: 10px;
  position: absolute;
  bottom: 1px;
  &[status="online"] {
    background-color: #22a559;
  }
  &[status="notice"] {
    background-color: #f23f43;
    width: 15px;
    height: 15px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 10px;
    font-weight: bold;
  }
  &[status="dnd"] {
    background-color: #f23f43;
    .border {
      border: 1.8px solid #2b2d31;
      border-radius: 10px;
      padding: 0px 3px;
    }
  }
  &[status="offline"] .border {
    border: 2px solid #80848e;
    border-radius: 10px;
    padding: 2px;
  }
}
</style>
