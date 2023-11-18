<script setup>
import { defineProps, ref, defineEmits, watch } from "vue";

const props = defineProps([
  "modelValue",
  "placeHolder",
  "required",
  "bottom",
  "data",
]);

const emit = defineEmits(["select", "input"]);

const dropdown = ref(false);
const items = ref(props.data || []);

const clone = items.value.reduce((acc, item) => {
  acc[item.key] = item.text;
  return acc;
}, {});
const searchItem = ref("");
const selectItem = ref();

watch(props, (newVal) => {
  selectItem.value = newVal.modelValue;
  items.value = newVal.data;
});

const onSearch = () => {
  items.value = Object.keys(clone)
    .filter((key) =>
      clone[key].toLowerCase().includes(searchItem.value.toLowerCase())
    )
    .map((key) => ({ key, text: clone[key] }));
};

const onSelect = (item) => {
  selectItem.value = item.key;
  dropdown.value = false;
  searchItem.value = "";
};
</script>

<template>
  <div id="discord-select">
    <div class="select-items" v-if="dropdown && items.length <= 0">
      <div class="select-item">{{ "No data found" }}</div>
    </div>
    <div class="select-items" v-if="dropdown">
      <div
        class="select-item"
        v-for="item of items"
        :key="item.key"
        @click="onSelect(item)">
        {{ item.text }}
      </div>
    </div>
    <div class="select-input" @click="dropdown = !dropdown" >
      <input
        v-model="searchItem"
        class="input"
        type="text"
        :required="props.required"
        @input="onSearch"
        :placeholder="selectItem ? clone[selectItem] : placeHolder" 
        />
      <span class="down-item material-icons" > expand_more </span>
    </div>
  </div>
</template>

<style lang="scss" scoped>
#discord-select {
  width: 100%;
  position: relative;
  cursor: pointer;
  transition: 1s all;
  display: block;
  .select-items {
    background-color: #313338;
    position: absolute;
    top: 38px;
    color: white;
    max-height: 200px;
    width: calc(100% - 2px);
    border: 1px solid #1e1f22;
    overflow: auto;
    z-index: 9999999;

    .select-item {
      padding: 10px;
      font-size: 14px;
      font-family: "gg sans", "Noto Sans", "Helvetica Neue", Helvetica, Arial,
        sans-serif;
      &:hover {
        background-color: #404249;
      }
    }
  }
  .select-input {
    position: relative;
    display: flex;
    align-items: center;
    .input {
      background-color: #1e1f22;
      padding: 10px;
      border: none;
      outline: none;
      color: white;
      width: calc(100% - 20px);
      font-size: 16px;
      border-radius: 3px;
      padding-right: 40px;
    }
    .down-item {
      position: absolute;
      right: 10px;
      color: white;
    }
  }
}
#discord-select.margin-have {
  margin-bottom: 20px;
}

#discord-select .label {
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
#discord-select .label .required {
  color: #9f393d;
  margin-left: 4px;
}
</style>
