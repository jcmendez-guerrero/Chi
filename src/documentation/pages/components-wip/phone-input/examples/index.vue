<template lang="pug">
  div
    h2 Examples

    <Base />
    <Placeholder />
    <DefaultCountry />
    <Value />
    <Disabled />
    <Error />
    <InputMask />
    div(v-if="$store.state.themes.theme === 'portal'")
      <SizesPortal />
    div(v-else)
      <SizesLumenCenturyLink />
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Base from './_base.vue';
import Placeholder from './_placeholder.vue';
import DefaultCountry from './_default-country.vue';
import Value from './_value.vue';
import Disabled from './_disabled.vue';
import Error from './_error.vue';
import SizesLumenCenturyLink from './_sizes_lumen_centurylink.vue';
import SizesPortal from './_portal/_sizes.vue';
import InputMask from './_input-mask.vue';

@Component({
  components: {
    Base,
    Placeholder,
    DefaultCountry,
    Value,
    Disabled,
    Error,
    SizesLumenCenturyLink,
    SizesPortal,
    InputMask
  }
})
export default class Examples extends Vue {}
</script>
