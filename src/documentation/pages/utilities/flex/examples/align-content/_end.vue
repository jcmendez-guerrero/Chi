<template lang="pug">
  <ComponentExample title="End" id="align-content-end" titleSize="h4" padding="-p--3" :tabs="exampleTabs" :showSnippetTabs="false">
    .-mb--2.-d--flex.-flex--wrap.-align-content--end.-show--example.-bg--grey-10(slot="example" style="height:12rem;")
      .-text.-p--2(v-for="i in 20" ) Item
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
        htmlblueprint: `<div class="-d--flex -align-content--end -flex--wrap">
  <div>Item</div>
</div>`
      }
    };
  }
})
export default class End extends Vue {}
</script>
