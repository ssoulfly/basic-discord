<script setup>
import Input from "../components/Input.vue";
import Button from "../components/Button.vue";
import Label from "../components/Label.vue";
import Background from "../components/svg/Background.vue";
import { useRouter, useRoute } from "vue-router";
const router = useRouter();

const selam = "";

const goRegisterPage = () => {
  router.push("/register");
};
</script>

<template>
  <div id="discord-home">
    
  </div>
</template>

<style scoped>
</style>
