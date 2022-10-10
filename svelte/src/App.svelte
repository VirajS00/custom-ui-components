<script lang="ts">
  import Button from './components/Button.svelte';
  import CheckBox from './components/CheckBox.svelte';
  import Select from './components/Select.svelte';
  import Switch from './components/Switch.svelte';
  import TextBox from './components/TextBox.svelte';
</script>

<main>
  <div class="container">
    <Select />
  </div>
  <div class="container">
    <TextBox name="test2" type="text" />
  </div>
  <div class="container">
    <CheckBox name="test" label="test" />
  </div>
  <div class="container">
    <Button>I am a button</Button>
  </div>
  <div class="container">
    <Switch name="test1" />
  </div>
</main>

<style lang="scss">
  main {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 0.5em;
    padding: 2em;
  }

  .container {
    border: 1px solid var(--clr-neutral-300);
    height: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 0.5em;
    padding: 0.5em;
  }
</style>
