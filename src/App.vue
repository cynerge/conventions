<template>
<div id="app">
  <SideMenu/>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> |
    <router-link to="/dropdowns">Dropdowns</router-link>
  </div>
  <router-view />
</div>
</template>

<script>
// @ is an alias to /src
import SideMenu from '@/components/layout/SideMenu.vue';

export default {
    name: 'App',
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
}

#nav {
    padding: 30px;

    a {
        font-weight: bold;
        color: #282551;

        &.router-link-exact-active {
            color: #282551; // $cyn-blue
        }
    }
}
</style>
