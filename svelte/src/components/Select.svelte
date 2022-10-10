<script lang="ts">
  import type { SelectOption } from 'src/helpers/types/selectOption';
  import { clickOutside } from '../helpers/clickOutside';

  export let options: SelectOption[];

  let show: boolean = false;
  let highlightedIndex = 0;
  let currentIndex: number = 0;

  const hideMenu = () => (show = !show);

  function handleClickOutside() {
    show = false;
  }

  const handleKeyDown = (e: KeyboardEvent) => {
    switch (e.key) {
      case 'Space':
        show = true;
      default:
        hideMenu();
    }
  };
</script>

<div
  class="select {show ? 'show' : ''}"
  role="listbox"
  tabindex="0"
  on:click={hideMenu}
>
  <div
    class="current-option {show ? 'show' : ''}"
    use:clickOutside
    on:click_outside={handleClickOutside}
    on:keydown={handleKeyDown}
  >
    {options[currentIndex].label}
  </div>
  <ul class="items {show ? '' : 'hidden'}">
    {#each options as option, i}
      <li on:mouseenter={() => (highlightedIndex = i)}>
        <button
          value={option.value}
          class={highlightedIndex === i ? 'highlited' : ''}
          on:click={() => {
            currentIndex = i;
            show = false;
          }}>{option.label}</button
        >
      </li>
    {/each}
  </ul>
</div>

<style lang="scss">
  .select {
    position: relative;
    border: 1px solid var(--clr-neutral-300);
    width: 100%;
    font-size: 1rem;
    border-radius: 0.25em;
    padding-inline: 0.7em;
    padding-block: 0.25em;
    outline: none;

    &:focus-visible {
      border-color: var(--clr-primary-400);
    }

    &.show {
      border-color: var(--clr-primary-500);
    }
  }

  .current-option {
    background-color: var(--clr-neutral-50);
    display: flex;
    align-items: center;
    justify-content: space-between;

    &::after {
      content: '';
      border: 0.25em solid transparent;
      border-top-color: var(--clr-neutral-400);
      transform: translateY(25%);
    }

    &.show {
      color: var(--clr-primary-500);
    }

    &.show::after {
      border-color: transparent;
      border-bottom-color: var(--clr-primary-500);
      transform: translateY(-25%);
    }
  }

  .items {
    position: absolute;
    list-style: none;
    padding-block: 0.25em;
    background-color: var(--clr-neutral-50);
    box-shadow: 0.2em 0 0.5em var(--clr-neutral-300);
    width: 100%;
    left: 0;
    top: calc(50% + 0.5em);
    z-index: 50;
    border-radius: 0.25em;
    border: 1px solid var(--clr-neutral-300);
    padding-inline: 0;

    li {
      margin: 0;

      button {
        padding-inline: 1em;
        padding-block: 0.7em;
        width: 100%;
        text-align: left;
        appearance: none;
        border: 0;
        background-color: var(--clr-neutral-50);
        cursor: pointer;
        font-size: 1rem;

        &.highlited {
          background-color: var(--clr-primary-100);
          color: var(--clr-primary-600);
        }
      }
    }

    &.hidden {
      display: none;
    }
  }
</style>
