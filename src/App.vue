<template>
  <img :class="{background: true, active:searchFocus}" src="./assets/background.webp" />
  <div class="cover"></div>
  <TimeVue />
  <SearchBarVue @search-focus="(searchFocus = true)" @search-unfocus="(searchFocus = false)" />
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Inter&display=swap');
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  font-family: -apple-system, "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", 'Inter', "Helvetica Neue", sans-serif;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

.cover {
  z-index: -1;
  opacity: 1;
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-image: radial-gradient(rgba(0,0,0,0) 0,rgba(0,0,0,.5) 100%),radial-gradient(rgba(0,0,0,0) 33%,rgba(0,0,0,.3) 166%);
  transition: .25s;
  background-color: rgba(0,0,0,.1);
}

.background {
  opacity: 1;
  z-index: -3;
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: opacity 1s, transform .25s, filter .25s;
  backface-visibility: hidden;
  &:is(.active) {
    transform: scale(1.1);
    filter: blur(10px);
  }
}

</style>
<script lang="ts">
import TimeVue from './components/TitleTime.vue';
import SearchBarVue from './components/SearchBar.vue';
export default {
  components: {TimeVue, SearchBarVue},
  data() {
    return {
      searchFocus: false
    }
  },
}
</script>