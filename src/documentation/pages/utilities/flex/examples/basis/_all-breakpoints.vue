<template lang="pug">
  div
    <TitleAnchor title="Target all breakpoints" id="basis-all-breakpoints" titleSize="h4"/>
    p.-text
      | Flex-basis utility classes with no breakpoint defined apply to all screen sizes.
    <TableComponent :data="getRows()" :columns="columns" additionalClasses="-bordered" />
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component({
  data: () => {
    return {
      columns: [
        {
          title: `Flex-basis Class`,
          key: 'cell1',
          width: '40%',
        },
        {
          title: 'Value',
          key: 'cell2',
          width: ''
        },
     ],
    };
  }
})
export default class AllBreakpoints extends Vue {
  types = ['auto', '0', '*'];

  getRows() {
    return this.types.map(type => ({
      cell1: `<code>-flex-basis--${type}</code>`,
      cell2: type === '*' ? 'can be incremented by 5%' : `<code>flex-basis: ${type};</code>`
    }))
  }
}
</script>
