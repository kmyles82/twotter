<template>
  <div id="app">
    <nav>
      <div class="navigation__logo">
        Twooter
      </div>
      <div class="navigation__user">
        {{ state.user.username }}
      </div>
    </nav>

    <router-view/>
  </div>
</template>

<script>
// import UserProfile from "@/views/UserProfile";

export default {
  name: "App",
  setup(){
    const state  = {
      user: {
        username: '__Kerry Myles'
      }
    }
    return {
      state
    }
  },
  components: {
    // UserProfile,
  },
  // data() {
  //   return {
  //     user: {
  //       username: '__Kerry Myles'
  //     }
  //   };
  // },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  min-height: 100vh;
  background-color: #F3F5FA;
  nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 5%;
    background-color: deeppink;
    color: white;
    .navigation__logo {
      font-weight: bold;
      font-size: 24px;
    }
    .navigation__user {
      font-weight: bold;
    }
  }
}
</style>
