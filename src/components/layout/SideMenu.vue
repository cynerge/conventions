<template>
    <div id="side-menu">
      <div v-on:click="expanded = !expanded" v-bind:class="{ 'expanded': expanded }" class="logo-container">
        <img class="side-menu-logo" alt="Cynerge logo" src="../../assets/cc_logo.png"/>
      </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'SideMenu',
    data() {
        return {
          expanded: false,
            users: null,
            selected: 'None',
            defaultSelected: 'Please select a user'
        };
    },
    created() {
        axios
            .get('https://jsonplaceholder.typicode.com/users')
            .then(res => {
                this.users = res.data;
            })
            .catch(err => {
                this.users = 'An error has occured: ' + err;
            });
    }
};
</script>

<style scoped lang="scss">
#side-menu {
  position: fixed;
  top: 0;
  left: 0;
  height: 100%;
  box-shadow: 0px 0px 5px 1px #7b7b7b;
  .logo-container {
    width: 55px;
    transition: all .33s ease;
    cursor: pointer;
    &.expanded {
      width: 250px;
    }
    .side-menu-logo {
      height: 40px;
      padding: 5px;
    }
  }
}

</style>
