<template lang="pug">
  div
    <TitleAnchor title="Target specific breakpoints" id="breakpoints-specific-vertical" />
    p.-text
      | To target a specific breakpoint, add the breakpoint abbreviation to the class. As Chi is a mobile first library, the value
      | will apply to that specific breakpoint and up.
    <TableComponent :columns="columns" :data="sizes" :getContent="getContent" />
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import { ITableColumn, ITableContent } from "~/models/models";
import { defaultColumns } from "~/fixtures/fixtures";

@Component({
  data: () => {
    return {
      columns: defaultColumns,
      sizes: [
        {
          name: 'sm',
          value: 'sm',
        },
        {
          name: 'md',
          value: 'md',
        },
        {
          name: 'lg',
          value: 'lg',
        },
        {
          name: 'xl',
          value: 'xl',
        }
      ]
    };
  },
})
export default class BreakpointsSpecific extends Vue {
  getContent(column: ITableColumn, content: ITableContent) {
    switch (column.key) {
      case 'class':
        return `<code>-vertical-align-${content.name}--middle</code>`;
      case 'value':
        return `<div class="-text">Vertical middle aligned on <code>${content.value}</code> and up.</div>`;
      default:
        return '';
    }
  };
}
</script>
