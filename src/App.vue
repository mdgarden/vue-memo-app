<template>
  <div id="app">
    <app-header />
    <memo-app/>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader';
import MemoApp from './components/MemoApp';

export default {
  name: 'app',
  components: {
    AppHeader,
    MemoApp
  }
};
</script>

<style>
@import "./styles/reset.css";
/* @import "./styles/styles.css"; */


#app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 560px;
  margin: 0 auto;;
}
</style>
