
<template>
  <div id="app">
    <div>
      <div class="wrapper">
              <sfolder
                :Dir="baseOfDir"
                />
      </div>
    </div>
  </div>
</template>

<script>

import json from '../public/static/node_modules.json';
import Sfolder from './components/Sfolder';

export default {
  name: 'App',
  components: {
    Sfolder
  },
  data: () => ({
    baseOfDir: json
  }),


}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
