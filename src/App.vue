<template>
  <div id="app">
    <app-file />
    ***************************************
    <hr>
    <hr>
    <hr>
    <app-multiple-files />
  </div>
</template>

<script>
import AppFile from './components/Elements/AppFile/AppFile.vue';
import AppMultipleFiles from './components/Elements/AppFile/AppMultipleFiles.vue';

export default {
  name: 'App',
  components: {
    AppFile,
    AppMultipleFiles,
  }
}
</script>

<style>

</style>
