<template>
  <div id="app">
    <v-main></v-main>
  </div>
</template>

<script>

import Main from './components/Main.vue';

export default {
  name: 'app',
  components: {
    'v-main': Main,
  },

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  font-family: Helvetica, Arial, sans-serif;
}

ul {
  padding: 0;
}

table {
  min-width: 300px;
  border: 1px solid #ccc;
  border-collapse: collapse;
}

td,th {
  max-width: 300px;
  border: 1px solid #ccc;
  padding: 5px 10px 5px 10px;
  text-align: left;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

th {
  cursor: pointer;
  user-select: none;
}

</style>
