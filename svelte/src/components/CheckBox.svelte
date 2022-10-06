<script lang="ts">
  import Fa from 'svelte-fa';
  import { faCheck } from '@fortawesome/free-solid-svg-icons';

  export let name: string;
  export let value: boolean = false;
  export let label: string;
  export let disabled: boolean = false;
</script>

<div class={disabled ? 'disabled' : ''}>
  <label for={name} class="icon-label {value ? 'checked' : ''}">
    <input
      type="checkbox"
      class="check"
      {name}
      id={name}
      bind:checked={value}
      {value}
      on:input={() => {
        value = !value;
      }}
      {disabled}
    />
    <span class="icon">
      <Fa
        icon={faCheck}
        color={disabled ? 'var(--clr-neutral-400)' : 'var(--clr-primary-400)'}
      />
    </span>
  </label>
  <label for={name} class="label1 {disabled ? 'disabled' : ''}">{label}</label>
</div>

<style lang="scss">
  div {
    display: inline-flex;
    gap: 0.5em;

    &.disabled {
      cursor: not-allowed;

      label {
        cursor: not-allowed;
      }

      & .icon-label.checked {
        background-color: var(--clr-neutral-300);
        border-color: var(--clr-neutral-400);
      }
    }
  }

  label {
    cursor: pointer;
  }

  .icon-label {
    --size: 25px;
    --duration: 150ms;

    position: relative;
    height: var(--size);
    width: var(--size);
    background-color: var(--clr-neutral-50);
    border: 0.1em solid var(--clr-neutral-300);
    border-radius: 0.3em;

    .icon {
      position: absolute;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100%;
      width: 100%;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%) scale(0.9);
      opacity: 0;
      transition: transform var(--duration) ease, opacity var(--duration) ease;
    }

    &.checked {
      background-color: var(--clr-primary-100);
      border: 0.1em solid var(--clr-primary-200);

      .icon {
        transform: translate(-50%, -50%) scale(1);
        opacity: 1;
      }
    }

    &:focus-within {
      border: 0.17em solid var(--clr-primary-300);
    }

    .check {
      transform: scale(0);
    }
  }

  .label1.disabled {
    color: var(--clr-neutral-400);
  }
</style>
