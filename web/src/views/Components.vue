<script setup>
import Button from "../components/Button.vue";
import Input from "../components/Input.vue";
import Label from "../components/Label.vue";
import ProfileImage from "../components/ProfilePhoto.vue";
import Select from "../components/Select.vue";
</script>
<template>
  <div>
    <Label text="Selam" />
    <Label text="Selam" :required="true" />
    <Input v-model="selam" :required="true" :bottom="true" />
    <Input v-model="selam" :required="true" />
    <Button text="Log In" />
    <div style="padding: 100px">
      <Select place-holder="Day" />
    </div>
    <ProfileImage text="sa" type="server" :notice-count="10" />
  </div>
  <!-- src="https://i.pinimg.com/originals/aa/db/17/aadb17c7e902874b914b3bef60c9b3d2.png" -->
</template>
