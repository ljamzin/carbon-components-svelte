<script>
  /**
   * Specify the selected tile value
   * @type {string} [selected]
   */
  export let selected = undefined;

  /**
   * Set to `true` to disable the tile group
   * @type {boolean} [disabled=false]
   */
  export let disabled = false;

  /**
   * Specify the legend text
   * @type {string} [legend]
   */
  export let legend = "";

  import { createEventDispatcher, setContext } from "svelte";
  import { writable } from "svelte/store";

  const dispatch = createEventDispatcher();
  const selectedValue = writable(selected);

  setContext("TileGroup", {
    selectedValue,
    add: ({ checked, value }) => {
      if (checked) {
        selectedValue.set(value);
      }
    },
    update: (value) => {
      selectedValue.set(value);
    },
  });

  $: selected = $selectedValue;
  $: dispatch("select", $selectedValue);
</script>

<fieldset {disabled} class:bx--tile-group={true} {...$$restProps}>
  {#if legend}
    <legend class:bx--label={true}>{legend}</legend>
  {/if}
  <div>
    <slot />
  </div>
</fieldset>
