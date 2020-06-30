<template>
  <div id="app">
    <div>{{count}}</div>
    <button @click="addCount">addCount</button>
  </div>
</template>

<script>
// import Setup from "./components/setup";
import { ref, onMounted, computed } from "@vue/composition-api";
export default {
  name: "App",
  components: {
    // Setup
  },
  beforeCreate() {
    console.log("我是beforeCreate");
  },
  setup() {
    console.log("我是setup钩子");
    const count = ref(0);
    const addCount = () => {
      count.value += 1;
    };
    const plusOne = computed(() => count.value + 5);
    onMounted(() => {
      count.value += plusOne.value;
      console.log("onMounted", plusOne.value);
    });
    return {
      count,
      addCount
    };
  },
  created() {
    console.log("我是create钩子");
  }
};
</script>

<style>
</style>
