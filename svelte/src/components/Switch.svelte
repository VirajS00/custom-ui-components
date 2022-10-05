<script lang="ts">
  export let name: string;
  export let value: boolean = false;
</script>

<label for={name} class={value ? 'checked' : ''}>
  <input
    type="checkbox"
    class="check"
    {name}
    id={name}
    {value}
    on:input={() => {
      value = !value;
    }}
  />
</label>

<style lang="scss">
  label {
    --height: 30px;
    --width: 60px;
    --initial-left: 3px;
    --duration: 150ms;

    position: relative;
    height: var(--height);
    width: var(--width);
    background-color: var(--clr-neutral-500);
    border-radius: 100vmax;
    cursor: pointer;

    &.checked {
      background-color: var(--clr-primary-500);

      &::before {
        transform: translate(
          calc(var(--width) - 100% - var(--initial-left)),
          -50%
        );
      }
    }

    &::before {
      content: '';
      position: absolute;
      top: 50%;
      transform: translate(var(--initial-left), -50%);
      border-radius: 50%;
      height: calc(var(--height) - 5px);
      width: calc(var(--height) - 5px);
      background-color: var(--clr-neutral-50);
      transition: transform var(--duration) ease;
    }

    .check {
      transform: scale(0);
    }
  }
</style>
