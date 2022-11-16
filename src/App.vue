<template>
  <div id="app">
    <nav>
      <h3 v-on:click="toggle_menu()">Phase 3 Media</h3>
      <router-link v-bind:style="menu_hidden" to="/">Home</router-link>
      
      <router-link v-bind:style="menu_hidden" to="/about">About</router-link>
      <router-link v-bind:style="menu_hidden" to="/contact">Contact</router-link>
    </nav>
    <router-view />
  </div>
</template>

<script>
// @ is an alias to /src



export default {
  name: 'HomeView',

  data() {
    return {
      menu_hidden: 'transform: translate3d(0, -50px, 0);'
    }
  },
  methods: {
    toggle_menu: function ()
    {
      if(this.menu_hidden == 'transform: translate3d(0, -50px, 0);')
      {
        this.menu_hidden = 'transform: translate3d(0, 0, 0);';
      }
      else
      {
        this.menu_hidden = 'transform: translate3d(0, -50px, 0);';
      }
    },
  },
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;


}

html {
  background-color: black;
}

nav {
  height: 50px;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
  position: fixed;
  top: 0%;
  width: 100%;
  z-index: 10000;
  h3 {
    font-weight:lighter;
    color: #ffffff;
    padding-left: 30px;
    padding-right: 30px;
    text-decoration: none;
    z-index: 100000;
    mix-blend-mode: difference;

  }

  h3:hover{
      font-weight: bolder;
      mix-blend-mode: difference;
  }
  a {
    font-weight: 50;
    color: #ffffff;
    padding-left: 30px;
    padding-right: 30px;
    text-decoration: none;
    transition: 1s all cubic-bezier(0.39, 0.575, 0.565, 1);

    &.router-link-exact-active {
      font-weight: bold;
      text-decoration: line-through;
      transition: 1s all cubic-bezier(0.39, 0.575, 0.565, 1);
    }
  }
}
</style>
