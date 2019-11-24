<template>
  <footer class="clearAllcontainer">
    <span class="clearAllbtn" v-on:click="clearTodo">Clear All</span>
  </footer>
</template>

<script>
export default {
  methods: {
    clearTodo() {
      this.$emit("clearAll");
    }
  }
};
</script>

<style scoped>
.clearAllcontainer {
  width: 8.5rem;
  height: 50px;
  line-height: 50px;
  background: #fff;
  border-radius: 5px;
  margin: 0 auto;
}
.clearAllbtn {
  display: block;
  color: #e20303;
  cursor: pointer;
}
</style>