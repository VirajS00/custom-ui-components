<script lang="ts">
  type ClickEventHandler = (event?: MouseEvent) => void;

  export let size: 'sm' | 'lg' | 'xs' | 'md' = 'sm';
  export let type: 'button' | 'submit' | 'reset' | 'menu' = 'button';
  export let onClick: ClickEventHandler | undefined = undefined;

  let ripple = false;

  const clickHandler: ClickEventHandler = e => {
    ripple = true;

    setTimeout(() => {
      ripple = false;
    }, 800);

    if (onClick) {
      onClick(e);
    }
  };

  let buttonWidth: number;
  let buttonHeight: number;
</script>

<button
  class="custom-button {size === 'sm'
    ? 'small'
    : size === 'lg'
    ? 'large'
    : size === 'md'
    ? 'medium'
    : 'extra-small'}
    
    {ripple ? 'ripple' : ''}"
  {type}
  bind:clientHeight={buttonHeight}
  bind:clientWidth={buttonWidth}
  on:click={clickHandler}
>
  <slot>Button</slot>
</button>

<style lang="scss">
  .custom-button {
    position: relative;
    background-color: var(--clr-primary-500);
    color: var(--clr-neutral-50);
    border: none;
    border-radius: 0.25em;
    cursor: pointer;
    padding-inline: 1.5em;
    padding-block: 0.625em;
    display: inline-flex;
    align-items: center;
    gap: 0.5em;
    overflow: hidden;

    &.small {
      font-size: 1rem;
    }

    &.large {
      font-size: 1.5rem;
    }

    &.extra-small {
      font-size: 0.8rem;
      padding-inline: 1em;
      padding-block: 0.5em;
    }

    &.medium {
      font-size: 1.25rem;
    }

    &:hover {
      background-color: var(--clr-primary-600);
    }

    &:active {
      background-color: var(--clr-primary-800);
    }

    &.ripple::after {
      content: '';
      position: absolute;
      width: 20px;
      height: 20px;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
      background: rgba(255, 255, 255, 0.497);
      display: block;
      border-radius: 50%;
      opacity: 1;
      animation: 800ms ease 1 forwards ripple-effect;
    }
  }

  @keyframes ripple-effect {
    0% {
      transform: scale(1);
      opacity: 1;
    }
    50% {
      transform: scale(10);
      opacity: 0.375;
    }
    100% {
      transform: scale(35);
      opacity: 0;
    }
  }
</style>
