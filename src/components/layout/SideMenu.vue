<template>
  <div class="side-menu">
    <div v-on:click="$emit('toggle-menu')" class="logo-container">
      <img class="side-menu-logo" alt="Cynerge logo" src="../../assets/cc_logo.png" />
    </div>
    <ul class="nav-items">
      <li v-for="item of items" v-bind:key="item.text">
        <span v-on:click="goTo(item.link)">{{item.text}}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'SideMenu',
  props: {
    items: Array
  },
  methods: {
    goTo: function(destination) {
      // router throws an error on attempts to navigate to the current location
      if (window.location.pathname !== destination) {
        this.$router.push({ path: destination })
      }
    }
  }
};
</script>

<style scoped lang="scss">
.side-menu {
  position: fixed;
  top: 0;
  left: 0;
  height: 100%;
  box-shadow: 0 0 5px 1px #7b7b7b;
  width: 55px;
  transition: all 0.33s ease;
  .logo-container {
    cursor: pointer;
    border-bottom: 1px solid lightgray;
    .side-menu-logo {
      transition: all .33s ease;
      height: 40px;
      padding: 5px;
    }
  }
  .nav-items {
    list-style: none;
    padding: 0;
    li {
      font-weight: bold;
      opacity: 0;
      color: rgba(255, 255, 255, 0);
      cursor: pointer;
      justify-content: center;
      display: flex;
      flex-direction: column;
      height: 50px;
      transition: all .33s ease;
    }
  }
  &.expanded {
    width: 250px;
    .logo-container {
      .side-menu-logo {
        height: 100px;
      }
    }
    .nav-items {
      li {
        opacity: 1;
        color: #282551;
      }
    }
  }
}
</style>
