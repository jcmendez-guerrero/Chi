<template lang="pug">
  header.docs-titlebar
    .chi-grid__container
      <h1 class="docs-titlebar__title">{{title}}</h1>
      .docs-titlebar__description(v-if="description") {{description}}
    <PageContentTabs v-if="$props.tabs" :tabs="$props.tabs" />
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import { Themes } from '../models/models';
import { ITabs } from '../models/models';

declare const chi: any;

@Component({})
export default class BaseExample extends Vue {
  @Prop() title?: string;
  @Prop() description?: string;
  @Prop() tabs?: ITabs[];

  theme: Themes = this.$store.state.themes.theme;
  chiTabs: any;

  mounted() {
    const chiTabs = document.getElementById('page-content-tabs');
    if (chiTabs) {
      this.chiTabs =  chi.tab(chiTabs);
    }
  }

  beforeDestroy() {
    this.chiTabs?.dispose();
  }
}
</script>
