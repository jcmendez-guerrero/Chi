<template lang="pug">
  div
    <TitleBar title="Position" description="Use shorthand position utility classes to quickly change an elements position value." />
    <Examples />
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Examples from './examples/index.vue'

@Component({
  head() {
    return {
      title: 'Chi - Position'
    }
  },
  components: {
    Examples
  }
})
export default class Position extends Vue {}
</script>
