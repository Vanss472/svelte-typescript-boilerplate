<!--
@component
  ### Button
  A button component, used primarily to triggers and event or action.

  - @props **className** string: 'default'.
  - @props **type** string: _'submit' | 'reset' | 'button'_.
  - @props **onClick** Function: () => void
  - @props **ariaLabel** string: 'Close'
-->
<script lang="ts">
  // your script goes here
  type ButtonProps = {
    // add a optional class to the button
    className?: string,
    // add a DOMString behavior for type
    type: "submit" | "reset" | "button",
    // add a handler to be called on click
    onClick?: () => void,
    // add a optional string value for aria-label
    ariaLabel?: string
  }

  export let btn: ButtonProps

</script>

<style lang="scss">
  /* your styles go here */
  button {
		border: 1px solid var(--btn-border);
		margin: 0;
		padding: 0;
		border-radius: 0;
		background: var(--btn-bg);
		appearance: none;
		text-decoration: none;
		cursor: pointer;
    color: var(--p-text);
    font-size: 1rem;
    padding-top: 10px;
    padding-bottom: 10px;
    padding-right: 20px;
    padding-left: 20px;

    &:focus,
    &:hover {
      color: var(--btn-text-hover);
      border-color: var(--btn-border-hover);
    }
	}
</style>

<!-- markup (zero or more items) goes here -->
<button
  class={btn.className}
  type={btn.type}
  on:click={btn.onClick}
  aria-label={btn.ariaLabel}
>
<!-- children content -->
  <slot></slot>
</button>