<template>
  <div id="app">
    <div id="nav">
      <router-link to="/universe"><v-btn>Read</v-btn></router-link>
      <router-link to="/planets-create"><v-btn>Create</v-btn></router-link>
      <router-link to="/planets-update"><v-btn>Update</v-btn></router-link>
      <router-link to="/planets-delete"><v-btn>Delete</v-btn></router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {},
  data: () => ({
    //
  }),
};
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
</style>
