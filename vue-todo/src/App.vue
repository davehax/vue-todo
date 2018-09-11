<template>
  <div id="app">
    <img src="./assets/logo.png">
    <TodoList />
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";

export default {
    name: "app",
    components: {
        TodoList
    },
    data() {
        return {
            msg: "Welcome to Your Vue.js App"
        };
    }
};
</script>

<style lang="scss">
*, *::before, *::after {
    box-sizing: border-box;
}

#app {
    font-family: Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: left;
    color: #2c3e50;
    margin-top: 60px;

    max-width: 600px;
    margin: 10vh auto;
}

img {
    display: block;
    width: 100px;
    text-align: center;
    margin: 20px auto;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  margin: 0 10px;

  justify-content: space-between;
  
}

a {
  color: #42b983;
}
</style>
