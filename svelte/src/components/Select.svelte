<script lang="ts"></script>

<div class="select" role="listbox" tabindex="0">
  <div class="current-option">Hello</div>
  <ul class="items">
    <li>Hello</li>
    <li>Hello 1</li>
    <li>Hello 2</li>
    <li>Hello 3</li>
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
      padding-inline: 0.7em;
      padding-block: 0.25em;
      margin: 0;
    }
  }
</style>
