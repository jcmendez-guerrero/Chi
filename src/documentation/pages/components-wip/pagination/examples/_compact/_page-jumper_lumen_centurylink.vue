<template lang="pug">
  <ComponentExample title="Page Jumper" id="compact-page-jumper-lumen-centurylink" :tabs="exampleTabs" padding="-p--0" titleSize="h4">
    .chi-grid.-no-gutter(slot="example")
      .chi-col.-w--12.-w-md--6(v-for="item in [1, 2]")
        .-p--3(:class="item === 2 ? '-bg--black' : ''")
          chi-pagination(pages="3" current-page="2" compact page-jumper :inverse="item === 2 ? true : false")
    <pre class="language-html" slot="code-webcomponent">
      <code v-highlight="$data.codeSnippets.webcomponent" class="html"></code>
    </pre>
    <pre class="language-html" slot="code-vue">
      <code v-highlight="$data.codeSnippets.vue" class="html"></code>
      </pre>
    <pre class="language-html" slot="code-htmlblueprint">
      <code v-highlight="$data.codeSnippets.htmlblueprint" class="html"></code>
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
          id: 'webcomponent',
          label: 'Web Component'
        },
         {
          id: 'vue',
          label: 'Vue'
        },
        {
          id: 'htmlblueprint',
          label: 'HTML Blueprint'
        }
      ],
      codeSnippets: {
        webcomponent: `<!-- For light backgrounds -->
<chi-pagination pages="3" current-page="2" compact page-jumper></chi-pagination>

<!-- For dark backgrounds -->
<chi-pagination pages="3" current-page="2" compact page-jumper inverse></chi-pagination>`,
        htmlblueprint: `<!-- For light backgrounds -->
<nav class="chi-pagination -compact" role="navigation" aria-label="Pagination">
  <div class="chi-pagination__content">
    <div class="chi-pagination__start"></div>
    <div class="chi-pagination__center">
      <div class="chi-pagination__button-group chi-button-group">
        <button class="chi-button -icon -flat -light" aria-label="Previous page" type="button">
          <div class="chi-button__content">
            <i class="chi-icon icon-chevron-left" aria-hidden="true"></i>
          </div>
        </button>
      </div>
      <div class="chi-pagination__jumper">
        <input type="text" class="chi-input" id="compact-jumper-input-2" aria-label="Page 2" value="2">
        <div class="chi-pagination__label">
          <span>of</span>
          <strong>3</strong>
        </div>
      </div>
      <div class="chi-pagination__button-group chi-button-group">
        <button class="chi-button -icon -flat -light" aria-label="Next page" type="button">
          <div class="chi-button__content">
            <i class="chi-icon icon-chevron-right" aria-hidden="true"></i>
          </div>
        </button>
      </div>
    </div>
    <div class="chi-pagination__end"></div>
  </div>
</nav>

<!-- For dark backgrounds -->
<nav class="chi-pagination -compact -inverse" role="navigation" aria-label="Pagination">
  <div class="chi-pagination__content">
    <div class="chi-pagination__start"></div>
    <div class="chi-pagination__center">
      <div class="chi-pagination__button-group chi-button-group">
        <button class="chi-button -icon -flat -light -md" aria-label="Previous page" type="button">
          <div class="chi-button__content">
            <i class="chi-icon icon-chevron-left" aria-hidden="true"></i>
          </div>
        </button>
      </div>
      <div class="chi-pagination__jumper">
        <input type="text" class="chi-input" id="compact-jumper-input-2" aria-label="Page 2" value="2">
        <div class="chi-pagination__label">
          <span>of</span>
          <strong>3</strong>
        </div>
      </div>
      <div class="chi-pagination__button-group chi-button-group">
        <button class="chi-button -icon -flat -light -md" aria-label="Next page" type="button">
          <div class="chi-button__content">
            <i class="chi-icon icon-chevron-right" aria-hidden="true"></i>
          </div>
        </button>
      </div>
    </div>
    <div class="chi-pagination__end"></div>
  </div>
</nav>`,
        vue: `<!-- For light backgrounds -->
<ChiPagination :pages="3" :currentPage="2" :compact="true" :pageJumper="true" />

<!-- For dark backgrounds -->
<ChiPagination :pages="3" :currentPage="2" :compact="true" :pageJumper="true" :inverse="true" />`
      }
    };
  }
})
export default class CompactPageJumperLumenCenturyLink extends Vue {}
</script>
