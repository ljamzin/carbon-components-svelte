<script>
  /**
   * Set to `true` to use as a header
   * @type {boolean} [head=false]
   */
  export let head = false;

  /**
   * Set to `true` to render a label slot
   * @type {boolean} [label=false]
   */
  export let label = false;

  /**
   * Specify the tabindex
   * @type {string} [tabindex="0"]
   */
  export let tabindex = "0";
</script>

{#if label}
  <label
    role="presentation"
    {tabindex}
    class:bx--structured-list-row={true}
    class:bx--structured-list-row--header-row={head}
    {...$$restProps}
    on:click
    on:mouseover
    on:mouseenter
    on:mouseleave
    on:keydown>
    <slot />
  </label>
{:else}
  <div
    class:bx--structured-list-row={true}
    class:bx--structured-list-row--header-row={head}
    {...$$restProps}
    on:click
    on:mouseover
    on:mouseenter
    on:mouseleave>
    <slot />
  </div>
{/if}
