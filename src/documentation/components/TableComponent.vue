<template>
  <section :class="['chi-table', additionalClasses]">
    <table class="-text">
      <thead>
      <tr>
        <th v-for="{ className, title } in tableColumns" :class="className" v-html="title" />
      </tr>
      </thead>
      <tbody>
      <tr v-for="content in data" :disabled="content.disabled" :class="content.className">
        <td v-for="column in tableColumns" :style="`width: ${column.width}`" :class="content[column.key]?.className">
          <span v-html="generateContent(column, content)" />
        </td>
      </tr>
      </tbody>
    </table>
  </section>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import { ITableColumn, ITableContent } from '~/models/models';

@Component({})
export default class TableComponent extends Vue {
  @Prop() columns?: ITableColumn[];
  @Prop({ default: [] }) data!: any[];
  @Prop(
    {
      type: Function,
      default: (column: ITableColumn, content: any) => content[column.key]
    }) getContent!: Function;
  @Prop({ default: '-mt--3 -mb--3 -bordered' }) additionalClasses?: string;
  @Prop() title?: string;

  get basicColumns() {
    return [
      {
        title: this.title ? this.title : 'Class',
        key: 'class',
        width: '25%'
      },
      {
        title: 'Value',
        key: 'value',
        width: '35%'
      },
      {
        title: 'Result',
        key: 'result',
        width: ''
      }
    ]
  }

  get tableColumns() {
    return this.columns ? this.columns : this.basicColumns;
  }

  generateContent(column: ITableColumn, content: ITableContent) {
    return this.getContent(column, content);
  }
}
</script>
