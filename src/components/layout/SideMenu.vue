<template>
  <div class="side-menu">
    <div v-on:click="$emit('toggle-menu')" class="logo-container">
      <img class="side-menu-logo" alt="Cynerge logo" src="../../assets/cc_logo.png" />
    </div>
    <ul class="nav-items">
      <li v-on:click="goTo(item)" v-bind:class="{ 'active': active === item.text }" v-for="item of items" v-bind:key="item.text">
        <span>{{item.text}}</span>
        <component class="nav-icon" :is="item.icon"></component>
        <!-- <img class="nav-icon" :src="require('../../assets/' + item.icon)" /> -->
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
  data() {
    return {
      active: ''
    }
  },
  methods: {
    goTo: function(destination) {
      // router throws an error on attempts to navigate to the current location
      if (window.location.pathname !== destination.link) {
        this.active = destination.text;
        this.$router.push({ path: destination.link })
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
    margin: 0;
    li {
      user-select: none;
      transition: all .2s linear;
      font-weight: bold;
      background-color: #ffffff;
      color: rgba(255, 255, 255, 0);
      cursor: pointer;
      justify-content: center;
      display: flex;
      flex-direction: row;
      align-items: center;
      height: 50px;
      span {
        transition: all .2s ease;
        opacity: 0;
        overflow: hidden;
        width: 0px;
      }
      .nav-icon {
        background-color: transparent;
        color: #282551;
        transition: all .33s ease;
        opacity: 1;
        height: 32px;
        width: 32px;
        position: relative;
        left: 0%;
      }
      &.active, &:active {
        background-color: #282551;
        color: #ff5500;
        span {
          color: #ff5500;
        }
        .nav-icon {
          color: #ff5500;
        }
      }
      &:hover {
        background-color: #ff5500;
        color: #282551;
        span {
          color: #282551;
        }
        .nav-icon {
          color: #282551;
        }
      }
    }
  }
  &.expanded {
    width: 250px;
    .logo-container {
      .side-menu-logo {
        height: 96px;
      }
    }
    .nav-items {
      li {
        color: #282551;
        span {
          opacity: 1;
          width: 250px;
        }
        .nav-icon {
          opacity: 0;
          height: 0px;
          width: 0px;
          left: -50%;
        }
      }
    }
  }
}
</style>
