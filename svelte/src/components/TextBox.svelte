<script lang="ts">
  export let name: string;
  export let value: string | undefined = undefined;
  export let placeholder = 'Enter text here';
  export let disabled: boolean = false;
</script>

<div class="tb-container">
  <input type="text" {name} id={name} bind:value {disabled} placeholder=" " />
  <label class="label" for={name}>{placeholder}</label>
</div>

<style lang="scss">
  .tb-container {
    --padding-inline: 0.5em;

    position: relative;
    border: 1px solid var(--clr-neutral-300);
    border-radius: 0.25em;
    width: 100%;
    height: 2.7em;
    background-color: var(--clr-neutral-50);

    .label,
    input {
      position: absolute;
    }

    input {
      appearance: none;
      outline: none;
      border: 0;
      z-index: 2;
      font-size: 1rem;
      border-radius: 0.25em;
      width: 100%;
      height: 100%;
      padding-inline: var(--padding-inline);
      background-color: transparent;
    }

    &:focus-within {
      border: 1px solid var(--clr-primary-500);
    }

    .label {
      display: flex;
      height: 100%;
      align-items: center;
      color: var(--clr-neutral-400);
      transform: translate(0.5em, 0) scale(1);
      transition: transform 250ms ease;
      padding-inline: 0.1em;
    }

    &:focus-within .label {
      transform: translate(calc(var(--padding-inline) / 2), -50%) scale(0.85);
      color: var(--clr-primary-500);
      background-color: var(--clr-neutral-50);
    }
  }

  input:not(:placeholder-shown):not(:focus) + .label {
    transform: translate(calc(var(--padding-inline) / 2), -50%) scale(0.85);
    background-color: var(--clr-neutral-50);
  }
</style>
