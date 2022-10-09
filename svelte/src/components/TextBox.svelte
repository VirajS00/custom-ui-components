<script lang="ts">
  export let name: string;
  export let type: 'text' | 'number' | 'url' | 'email' | 'password' = 'text';
  export let value: string | undefined = undefined;
  export let disabled: boolean = false;
  export let hasError: boolean = false;

  export let onblur: (e?: FocusEvent) => void | undefined = undefined;
  export let onfocus: (e?: FocusEvent) => void | undefined = undefined;
  export let onchange: () => void | undefined = undefined;
  export let oninput: (e?: any) => void | undefined = undefined;
  export let placeholder = `Enter ${type} here`;
  export let max: number | undefined = undefined;
  export let min: number | undefined = undefined;
  export let pattern: string | undefined = undefined;
  export let spellcheck: boolean = true;
  export let autocapitalize:
    | 'off'
    | 'none'
    | 'on'
    | 'sentences'
    | 'words'
    | 'characters' = 'none';
  export let autocomplete: boolean = false;
  export let maxlength: number | undefined = undefined;
  export let onpaste: () => void | undefined = undefined;
  export let onkeydown: (e?: KeyboardEvent) => void | undefined = undefined;
</script>

<div class="tb-container {hasError ? 'error' : ''}">
  {#if type === 'text'}
    <input
      type="text"
      {name}
      id={name}
      bind:value
      {disabled}
      placeholder=" "
      on:blur={onblur}
      on:focus={onfocus}
      on:change={onchange}
      on:input={oninput}
      {max}
      {min}
      {pattern}
      {spellcheck}
      {autocapitalize}
      autocomplete={autocomplete ? 'on' : 'off'}
      {maxlength}
      on:paste={onpaste}
      on:keydown={onkeydown}
    />
  {:else if type === 'email'}
    <input
      type="email"
      {name}
      id={name}
      bind:value
      {disabled}
      placeholder=" "
      on:blur={onblur}
      on:focus={onfocus}
      on:change={onchange}
      on:input={oninput}
      {max}
      {min}
      {pattern}
      {spellcheck}
      {autocapitalize}
      autocomplete={autocomplete ? 'on' : 'off'}
      {maxlength}
      on:paste={onpaste}
      on:keydown={onkeydown}
    />
  {:else if type === 'number'}
    <input
      type="number"
      {name}
      id={name}
      bind:value
      {disabled}
      placeholder=" "
      on:blur={onblur}
      on:focus={onfocus}
      on:change={onchange}
      on:input={oninput}
      {max}
      {min}
      {pattern}
      {maxlength}
      on:paste={onpaste}
      on:keydown={onkeydown}
    />
  {:else if type === 'password'}
    <input
      type="password"
      {name}
      id={name}
      bind:value
      {disabled}
      placeholder=" "
      on:blur={onblur}
      on:focus={onfocus}
      on:change={onchange}
      on:input={oninput}
      {max}
      {min}
      {pattern}
      {spellcheck}
      {autocapitalize}
      autocomplete={autocomplete ? 'on' : 'off'}
      {maxlength}
      on:paste={onpaste}
      on:keydown={onkeydown}
    />
  {:else}
    <input
      type="url"
      {name}
      id={name}
      bind:value
      {disabled}
      placeholder=" "
      on:blur={onblur}
      on:focus={onfocus}
      on:change={onchange}
      on:input={oninput}
      {max}
      {min}
      {pattern}
      {spellcheck}
      {autocapitalize}
      autocomplete={autocomplete ? 'on' : 'off'}
      {maxlength}
      on:paste={onpaste}
      on:keydown={onkeydown}
    />
  {/if}

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

    &:hover {
      border-color: var(--clr-primary-600);
    }

    &:hover .label {
      color: var(--clr-primary-600);
    }

    &.error:focus-within .label {
      color: var(--clr-error-500);
    }

    &.error {
      border: 1px solid var(--clr-error-500);
    }

    &.error label {
      color: var(--clr-error-500);
    }

    &.error input {
      color: var(--clr-error-500);
    }

    &.error:hover {
      border-color: var(--clr-error-600);
    }

    &.error:hover .label {
      color: var(--clr-error-600);
    }

    &.error:hover input {
      color: var(--clr-error-600);
    }
  }

  input:not(:placeholder-shown):not(:focus) + .label {
    transform: translate(calc(var(--padding-inline) / 2), -50%) scale(0.85);
    background-color: var(--clr-neutral-50);
  }
</style>
