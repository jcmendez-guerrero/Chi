<template lang="pug">
  <ComponentExample title="No Wrap (default)" id="no-wrap" titleSize="h4" padding="-p--3" :tabs="exampleTabs" :showSnippetTabs="false">
    .-mb--2.-d--flex.-flex--nowrap.-align-items--start.-show--example.-bg--grey-10(slot="example" style="height:116px;width:224px;")
      .-text.-p--2(v-for="i in 4" ) Item
    <pre class="language-html" slot="code-htmlblueprint">
      <code v-highlight="codeSnippets.htmlblueprint" class="html"></code>
    </pre>
  </ComponentExample>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component({
  data: () => {
    return {
      exampleTabs: [
        {
          active: true,
          id: 'htmlblueprint',
          label: 'HTML Blueprint'
        }
      ],
      codeSnippets: {
        htmlblueprint: `<div class="-d--flex -align-items--start -flex--nowrap" style="height:116px;width:224px;">
  <div>Item</div>
</div>`
      }
    };
  }
})
export default class NoWrap extends Vue {}
</script>
