<template>
  <div id="app">
    <InfluencerList />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import InfluencerList from '@/components/InfluencerList.vue';

export default Vue.extend({
  name: 'App',
  components: { InfluencerList },
});
</script>

<style>
body {
  background-color: #fafafa;
}

#app {
  font-family:             "Droid Sans", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing:  antialiased;
  -moz-osx-font-smoothing: grayscale;
  color:                   #2c3e50;
  margin-top:              60px;
  display:                 flex;
  justify-content:         center;
}
</style>
