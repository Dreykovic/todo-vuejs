<template>
  <div id="app">
    <h4 class="title">{{ name }}'s To Do List</h4>
  </div>
</template>
<script>
export default {
  name: "app",
  data() {
    return {
      name: "Audrey",
    };
  },
};
</script>
<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  background: dodgerblue;
}
#app > h4.title {
  text-align: center;
  color: white;
  font-size: large;
}
</style>