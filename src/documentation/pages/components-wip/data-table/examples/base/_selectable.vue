<template lang="pug">
  div
    <ComponentExample title="Selectable" id="selectable-data-table" :tabs="exampleTabs">
      chi-data-table(:config='config', :data='table' slot="example")
      <Wrapper slot='code-vue'>
        .chi-tab__description
          | Use <code>selectable</code> config to render rows with selectable checkboxes
        pre.language-html
          code(v-highlight="getRadioSelectionVueCode(true)" class="html")
      </Wrapper>
      pre.language-html(slot="code-htmlblueprint")
        code(v-highlight="codeSnippets.htmlblueprintCheckbox" class="html")
    </ComponentExample>

    <ComponentExample title="Radio Selection" id="radio-selection-data-table" :tabs="exampleTabs">
      chi-data-table(:config='getRadioSelectionConfig()', :data='table' slot="example")
      <Wrapper slot='code-vue'>
        .chi-tab__description
          | Use <code>selectable</code> config to render rows with radio buttons
        pre.language-html
          code(v-highlight="getRadioSelectionVueCode('radio')" class="html")
      </Wrapper>
      pre.language-html(slot="code-htmlblueprint")
        code(v-highlight="codeSnippets.htmlblueprintRadio" class="html")
    </ComponentExample>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component({
  data: () => {
    return {
      exampleTabs: [
        {
          active: false,
          id: 'webcomponent',
          label: 'Web Component',
          disabled: true
        },
        {
          active: true,
          id: 'vue',
          label: 'Vue',
        },
        {
          active: false,
          id: 'htmlblueprint',
          label: 'HTML Blueprint',
        }
      ],
      config: {
        columnResize: true,
        style: {
          portal: false,
          noBorder: false,
          bordered: false,
          hover: false,
          size: 'md',
          striped: false,
        },
        pagination: {
          activePage: 1,
          compact: false,
          firstLast: false,
          pageJumper: true,
        },
        selectable: true,
        showSelectAllDropdown: true,
        resultsPerPage: 3,
      },
      table: {
        head: {
          name: { label: 'Name' },
          id: { label: 'ID' },
          lastLogin: { label: 'Last Login' },
        },
        body: [
          {
            id: 'name-1',
            data: [
              'Name 1',
              'name-1',
              '18 Dec 2020 3:26 p.m.',
            ],
          },
          {
            id: 'name-2',
            data: [
              'Name 2',
              'name-2',
              '18 Dec 2020 2:38 a.m.',
            ],
          },
          {
            id: 'name-3',
            data: [
              'Name 3',
              'name-3',
              '5 Nov 2020 10:15 a.m.',
            ],
          },
          {
            id: 'name-4',
            data: [
              'Name 4',
              'name-4',
              '18 Dec 2020 3:26 p.m.',
            ],
          },
          {
            id: 'name-5',
            data: [
              'Name 5',
              'name-5',
              '18 Dec 2020 2:38 a.m.',
            ],
          },
          {
            id: 'name-6',
            data: [
              'Name 6',
              'name-6',
              '5 Nov 2020 10:15 a.m.',
            ],
          },
        ]
      },
      codeSnippets: {
        htmlblueprintRadio: `<div class="chi-data-table">
  <div class="chi-data-table__head">
    <div class="chi-data-table__row">
      <div class="chi-data-table__cell -selectable"></div>
      <div class="chi-data-table__cell">
        <div>Name</div>
      </div>
      <div class="chi-data-table__cell">
        <div>ID</div>
      </div>
      <div class="chi-data-table__cell">
        <div>Last Login</div>
      </div>
    </div>
  </div>
  <div class="chi-data-table__body">
    <fieldset>
      <legend class="--sr-only">Select a Row</legend>
      <div class="chi-data-table__row">
        <div class="chi-data-table__cell -selectable">
          <div class="chi-radio">
            <input type="radio" class="chi-radio__input" id="radio-ba2" name="radios">
            <label class="chi-radio__label" for="radio-ba2"></label>
          </div>
        </div>
        <div class=" chi-data-table__cell" data-label="Name">
          <div>Name 1</div>
        </div>
        <div class="chi-data-table__cell" data-label="ID">
          <div>name-1</div>
        </div>
        <div class="chi-data-table__cell" data-label="Last Login">
          <div>18 Dec 2020 3:26 p.m.</div>
        </div>
      </div>
      <div class="chi-data-table__row -selected">
        <div class="chi-data-table__cell -lh--1 -selectable">
          <div class="chi-radio">
            <input type="radio" class="chi-radio__input" id="radio-ba3" name="radios">
            <label class="chi-radio__label" for="radio-ba3"></label>
          </div>
        </div>
        <div class=" chi-data-table__cell" data-label="Name">
          <div>Name 2</div>
        </div>
        <div class="chi-data-table__cell" data-label="ID">
          <div>name-2</div>
        </div>
        <div class="chi-data-table__cell" data-label="Last Login">
          <div>18 Dec 2020 2:38 a.m.</div>
        </div>
      </div>
      <div class="chi-data-table__row">
        <div class="chi-data-table__cell -lh--1 -selectable">
          <div class="chi-radio">
            <input type="radio" class="chi-radio__input" id="radio-ba4" name="radios">
            <label class="chi-radio__label" for="radio-ba4"></label>
          </div>
        </div>
        <div class=" chi-data-table__cell" data-label="Name">
          <div>Name 3</div>
        </div>
        <div class="chi-data-table__cell" data-label="ID">
          <div>name-3</div>
        </div>
        <div class="chi-data-table__cell" data-label="Last Login">
          <div>5 Nov 2020 10:15 a.m.</div>
        </div>
      </div>
    </fieldset>
  </div>
  <div class="chi-data-table__footer">
    <nav class="chi-pagination" role="navigation" aria-label="Pagination">
      <div class="chi-pagination__content">
        <div class="chi-pagination__start">
          <div class="chi-pagination__results">
            <span class="chi-pagination__label">240 results</span>
          </div>
          <div class="chi-pagination__page-size">
            <div class="chi-dropdown">
              <button class="chi-button -flat -px--1 chi-dropdown__trigger" id="pagesize-7">20</button>
              <div class="chi-dropdown__menu -w--xs">
                <a class="chi-dropdown__menu-item -active" href="#">20</a>
                <a class="chi-dropdown__menu-item" href="#">40</a>
                <a class="chi-dropdown__menu-item" href="#">60</a>
                <a class="chi-dropdown__menu-item" href="#">80</a>
                <a class="chi-dropdown__menu-item" href="#">All</a>
              </div>
            </div>
            <span class="chi-pagination__label">per page</span>
          </div>
        </div>
        <div class="chi-pagination__center">
          <div class="chi-pagination__button-group chi-button-group">
            <button class="chi-button -icon -flat" aria-label="Previous page">
              <div class="chi-button__content">
                <i class="chi-icon icon-chevron-left" aria-hidden="true"></i>
              </div>
            </button>
            <button class="chi-button -flat" aria-label="Page 1">1</button>
            <button class="chi-button -flat" aria-label="Page 2">2</button>
            <button class="chi-button -flat -active" aria-label="Page 3">3</button>
            <button class="chi-button -flat" aria-label="Page 4">4</button>
            <button class="chi-button -flat" aria-label="Page 5">5</button>
            <div class="chi-button -flat" aria-hidden="true" disabled>...</div>
            <button class="chi-button -flat" aria-label="Page 12">12</button>
            <button class="chi-button -icon -flat" aria-label="Next page">
              <div class="chi-button__content">
                <i class="chi-icon icon-chevron-right" aria-hidden="true"></i>
              </div>
            </button>
          </div>
        </div>
        <div class="chi-pagination__end">
          <div class="chi-pagination__jumper">
            <label class="chi-pagination__label" for="jumper-input-7">Go to page:</label>
            <input class="chi-input" type="text" id="jumper-input-7" />
          </div>
        </div>
      </div>
    </nav>
  </div>
</div>`,
        htmlblueprintCheckbox: `<div class="chi-data-table">
  <div class="chi-data-table__head">
    <div class="chi-data-table__row">
      <div class="chi-data-table__cell -selectable">
        <div class="chi-checkbox">
          <input type="checkbox" class="chi-checkbox__input" id="checkbox-ba1">
          <label class="chi-checkbox__label" for="checkbox-ba1">
            <div class="-sr--only">Label</div>
          </label>
        </div>
        <div class="chi-dropdown">
          <button aria-label="Select All Dropdown" data-position="bottom-start" class="chi-button -icon -flat -has-active">
            <div class="chi-button__content">
              <i aria-hidden="true" class="chi-icon icon-chevron-down -xs"></i>
            </div>
          </button>
          <div class="chi-dropdown__menu" x-placement="bottom-start">
            <a class="chi-dropdown__menu-item">Select all items, this page</a>
            <a class="chi-dropdown__menu-item">Select all items, all pages</a>
            <a class="chi-dropdown__menu-item">Deselect all</a>
          </div>
        </div>
      </div>
      <div class="chi-data-table__cell">
        <div>Name</div>
      </div>
      <div class="chi-data-table__cell">
        <div>ID</div>
      </div>
      <div class="chi-data-table__cell">
        <div>Last Login</div>
      </div>
    </div>
  </div>
  <div class="chi-data-table__body">
    <div class="chi-data-table__row">
      <div class="chi-data-table__cell -selectable">
        <div class="chi-checkbox">
          <input type="checkbox" class="chi-checkbox__input" id="checkbox-ba2">
          <label class="chi-checkbox__label" for="checkbox-ba2">
            <div class="-sr--only">Label</div>
          </label>
        </div>
      </div>
      <div class="chi-data-table__cell" data-label="Name">
        <div>Name 1</div>
      </div>
      <div class="chi-data-table__cell" data-label="ID">
        <div>name-1</div>
      </div>
      <div class="chi-data-table__cell" data-label="Last Login">
        <div>18 Dec 2020 3:26 p.m.</div>
      </div>
    </div>
    <div class="chi-data-table__row -selected">
      <div class="chi-data-table__cell -lh--1 -selectable">
        <div class="chi-checkbox">
          <input type="checkbox" class="chi-checkbox__input" id="checkbox-ba3">
          <label class="chi-checkbox__label" for="checkbox-ba3">
            <div class="-sr--only">Label</div>
          </label>
        </div>
      </div>
      <div class="chi-data-table__cell" data-label="Name">
        <div>Name 2</div>
      </div>
      <div class="chi-data-table__cell" data-label="ID">
        <div>name-2</div>
      </div>
      <div class="chi-data-table__cell" data-label="Last Login">
        <div>18 Dec 2020 2:38 a.m.</div>
      </div>
    </div>
    <div class="chi-data-table__row">
      <div class="chi-data-table__cell -lh--1 -selectable">
        <div class="chi-checkbox">
          <input type="checkbox" class="chi-checkbox__input" id="checkbox-ba4">
          <label class="chi-checkbox__label" for="checkbox-ba4">
            <div class="-sr--only">Label</div>
          </label>
        </div>
      </div>
      <div class="chi-data-table__cell" data-label="Name">
        <div>Name 3</div>
      </div>
      <div class="chi-data-table__cell" data-label="ID">
        <div>name-3</div>
      </div>
      <div class="chi-data-table__cell" data-label="Last Login">
        <div>5 Nov 2020 10:15 a.m.</div>
      </div>
    </div>
  </div>
  <div class="chi-data-table__footer">
    <nav class="chi-pagination" role="navigation" aria-label="Pagination">
      <div class="chi-pagination__content">
        <div class="chi-pagination__start">
          <div class="chi-pagination__results">
            <span class="chi-pagination__label">240 results</span>
          </div>
          <div class="chi-pagination__page-size">
            <div class="chi-dropdown">
              <button class="chi-button -flat -px--1 chi-dropdown__trigger" id="pagesize-7">20</button>
              <div class="chi-dropdown__menu -w--xs">
                <a class="chi-dropdown__menu-item -active" href="#">20</a>
                <a class="chi-dropdown__menu-item" href="#">40</a>
                <a class="chi-dropdown__menu-item" href="#">60</a>
                <a class="chi-dropdown__menu-item" href="#">80</a>
                <a class="chi-dropdown__menu-item" href="#">All</a>
              </div>
            </div>
            <span class="chi-pagination__label">per page</span>
          </div>
        </div>
        <div class="chi-pagination__center">
          <div class="chi-pagination__button-group chi-button-group">
            <button class="chi-button -icon -flat" aria-label="Previous page">
              <div class="chi-button__content">
                <i class="chi-icon icon-chevron-left" aria-hidden="true"></i>
              </div>
            </button>
            <button class="chi-button -flat" aria-label="Page 1">1</button>
            <button class="chi-button -flat" aria-label="Page 2">2</button>
            <button class="chi-button -flat -active" aria-label="Page 3">3</button>
            <button class="chi-button -flat" aria-label="Page 4">4</button>
            <button class="chi-button -flat" aria-label="Page 5">5</button>
            <div class="chi-button -flat" aria-hidden="true" disabled>...</div>
            <button class="chi-button -flat" aria-label="Page 12">12</button>
            <button class="chi-button -icon -flat" aria-label="Next page">
              <div class="chi-button__content">
                <i class="chi-icon icon-chevron-right" aria-hidden="true"></i>
              </div>
            </button>
          </div>
        </div>
        <div class="chi-pagination__end">
          <div class="chi-pagination__jumper">
            <label class="chi-pagination__label" for="jumper-input-7">Go to page:</label>
            <input class="chi-input" type="text" id="jumper-input-7" />
          </div>
        </div>
      </div>
    </nav>
  </div>
</div>`,
      },
    };
  },
  methods: {
    getRadioSelectionConfig() {
      return {
        ...this.$data.config,
        selectable: 'radio'
      };
    },
    getRadioSelectionVueCode(selection: boolean | 'radio') {
      return `<!-- Vue component -->
<ChiDataTable :config="config" :data="table"></ChiDataTable>

<!-- Config and Data -->
data: {
  config: {
    columnResize: true,
    style: {
      portal: false,
      noBorder: false,
      bordered: false,
      hover: false,
      size: 'md',
      striped: false,
    },
    pagination: {
      activePage: 1,
      compact: false,
      firstLast: false,
      pageJumper: true,
    },
    selectable: ${selection === 'radio' ? `'radio'` : `${selection}
    showSelectAllDropdown: true`},
    resultsPerPage: 3,
  },
  table: {
    head: {
      name: { label: 'Name' },
      id: { label: 'ID' },
      lastLogin: { label: 'Last Login' },
    },
    body: [
      {
        id: 'name-1',
        data: [
          'Name 1',
          'name-1',
          '18 Dec 2020 3:26 p.m.',
        ],
      },
      {
        id: 'name-2',
        data: [
          'Name 2',
          'name-2',
          '18 Dec 2020 2:38 a.m.',
        ],
      },
      {
        id: 'name-3',
        data: [
          'Name 3',
          'name-3',
          '5 Nov 2020 10:15 a.m.',
        ],
      },
      {
        id: 'name-4',
        data: [
          'Name 4',
          'name-4',
          '18 Dec 2020 3:26 p.m.',
        ],
      },
      {
        id: 'name-5',
        data: [
          'Name 5',
          'name-5',
          '18 Dec 2020 2:38 a.m.',
        ],
      },
      {
        id: 'name-6',
        data: [
          'Name 6',
          'name-6',
          '5 Nov 2020 10:15 a.m.',
        ],
      },
    ]
  }
}`
    }
  }
})
export default class DataTableSelectable extends Vue { }
</script>
