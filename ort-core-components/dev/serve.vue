<script>
import Vue from 'vue';
// Uncomment import and local "components" registration if library is not registered globally.
// import { OrtCoreComponentsSample } from '@/entry.esm';
import { Button } from '@/entry.esm';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    Button,
  }
});
</script>

<template>
  <div id="app">
    <ort-core-components-sample />
    <Button />
  </div>
</template>
