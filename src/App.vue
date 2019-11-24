<template>
  <div id="app">
    <SideMenu v-bind:class="{ 'expanded': expanded }" v-on:toggle-menu="expanded = !expanded" :items="navItems"></SideMenu>
    <router-view v-bind:class="{ 'expanded': expanded }" class="main-view" />
  </div>
</template>

<script>
// @ is an alias to /src
import SideMenu from '@/components/layout/SideMenu.vue';

export default {
  name: 'App',
  data() {
    return {
      expanded: true,
      navItems: [{
        text: 'Home',
        link: '/'
      }, {
        text: 'About',
        link: '/about',
      }, {
        text: 'Components',
        link: '/dropdowns'
      }]
    };
  },
  components: {
    SideMenu
  }
};
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #282551;
  .main-view {
    transition: all .33s ease-in-out;
    position: fixed;
    top: 0;
    left: 55px;
    width: calc(100% - 55px);
    &.expanded {
      left: 250px;
      width: calc(100% - 250px);
    }
  }
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #282551;
    &.router-link-exact-active {
      color: #282551;
    }
  }
}
</style>
