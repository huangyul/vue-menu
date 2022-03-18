<template>
  <div id="app">
    <my-menu style="width: 200px"></my-menu>
  </div>
</template>

<script>
  /* eslint-disable */
  import MyMenu from './components/MyMene.vue'

  export default {
    name: 'App',
    components: { MyMenu },
    data() {
      return {
        // 菜单数据
        menuData: [
          {
            title: '菜单1',
            value: '1',
          },
          {
            title: '菜单2',
            value: '2',
          },
        ],
      }
    },
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
