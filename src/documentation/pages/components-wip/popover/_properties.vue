<template lang="pug">
  div
    h2 Web Component
    <PropertiesGenerator tag="chi-popover" />

    .chi-divider.-my--5

    h2 JavaScript
    p.-text This component accepts options to configure its behavior.

    section.chi-table.chi-table__options.-bordered.-my--3
      div
        table.-text(cellpadding='0', cellspacing='0')
          thead
            tr
              th
                div Option
              th
                div Default
              th
                div Description
          tbody
            tr
              td
                div
                  code= 'animate'
              td
                div
                  code= 'true'
              td
                div
                  | Enables animation on popover display and hide.
            tr
              td
                div
                  code= 'content'
              td
                div
                  code= 'null'
              td
                div
                  | Lets the developer include the popover content programmatically on the creation phase.
            tr
              td
                div
                  code= 'position'
              td
                div
                  code 'top'
              td
                div
                  | Where the popover will be located by default. If there is no free space in that position, the popover will try
                  | to flip the position to the opposite side. <code>data-position</code> takes precedence over this configuration
                  | option.
            tr
              td
                div
                  code= 'arrow'
              td
                div
                  code= 'true'
              td
                div
                  | If set to true, an arrow will appear between the popover and the trigger element.
            tr
              td
                div
                  code= 'parent'
              td
                div
                  code= 'null'
              td
                div
                  | If an element is provided as parent, the popover will be attached visually to that element. If not, the
                  | popover will be attached to the trigger used in instantiation.
            tr
              td
                div
                  code= 'classes'
              td
                div
                  code= '[]'
              td
                div
                  | Lets the developer add any classes to the popover element in the creation phase.
            tr
              td
                div
                  code= 'trigger'
              td
                div
                  code 'click'
              td
                div
                  | Available options are <code>click</code> or <code>manual</code>. Use click to attach the toggle action
                  | to the trigger element, and manual for develop a custom solution.
            tr
              td
                div
                  code= 'target'
              td
                div
                  code 'null'
              td
                div
                  | If you specify a target, the Popover will be build over that Element. You can specify the xpath selector
                  | of the element or the element itself.
            tr
              td
                div
                  code= 'preventAutoHide'
              td
                div
                  code= 'false'
              td
                div
                  | Set <code>preventAutoHide</code> to <code>true</code> to prevent hidding the popover when clicking
                  | outside the popover.

    h3 Methods
    h4 .setContent()
    p.-text
      | Use this method to change the content of the popover. It discards any previously attached content, so any
      | resources attached to the content should be removed to prevent memory leaks. This method accepts a string or an
      | HTML DOM Element as a parameter.
    .example.-mb--3
      .-p--3
        button.chi-button.-mb--2(ref="button" data-popover-content="<div class='chi-popover__content'>Foo</div>") Popover
        <pre class="language-javascript">
          <code v-highlight="$data.example" class="javascript"></code>
        </pre>

    h3 Events
    section.chi-table.-bordered.-my--3
      table(cellpadding='0', cellspacing='0')
        thead
          tr
            th
              div Event
            th
              div Description
        tbody
          tr
            td
              div
                code chiPopoverShow
            td
              div Popover show has been triggered, but the showing animation has not started yet.
          tr
            td
              div
                code chiPopoverHide
            td
              div Popover hide has been triggered, but the closing animation has not started yet.
          tr
            td
              div
                code chiPopoverShown
            td
              | Popover has been shown to the user and is fully visible. The animation has completed.
          tr
            td
              div
                code chiPopoverHidden
            td
              div
                | Popover has been hidden to the user. The animation has completed.

    h3 Preventing memory leaks
    p.-text
      | Popover components have a dispose function to free all resources attached to the element, such as event listeners
      | and object data. You must call this method when you want to remove the component.
    <pre class="language-javascript">
      <code v-highlight="$data.codeMemory1" class="javascript"></code>
    </pre>

    p.-text
      | It is safe to call the <code>popover</code> method more than once, as it will return any previously created popover component
      | associated with the trigger.
    <pre class="language-javascript">
      <code v-highlight="$data.codeMemory2" class="javascript"></code>
    </pre>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

declare const chi: any;

@Component({
  data: () => {
    return {
      example: `<button id='popover-2' class="chi-button" data-popover-content='<div class="chi-popover__content">Foo</div>'>Popover</button>
<script>
  var popover = chi.popover(document.getElementById('popover-2'));
  popover.setContent('<div class="chi-popover__content">Bar</div>');
<\/script>`,
      codeMemory1: `var elem = document.getElementById('popover');
var popover = chi.popover(elem);
// do stuff
popover.dispose();`,
      codeMemory2: `var elem = document.getElementById('popover-1');
var popover = chi.popover(elem);
var elem2 = document.getElementById('popover-1');
var popover2 = chi.popover(elem2);
popover === popover2; // returns true

popover.dispose(); // Only have to do it once.`
    };
  }
})
export default class Properties extends Vue {
  mounted() {
    const popover = chi.popover(this.$refs.button);

    popover.setContent('<div class="chi-popover__content">Bar</div>');
  }
}
</script>
