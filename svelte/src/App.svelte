<script lang="ts">
  import Switch from './components/Switch.svelte';
</script>

<main>
  <div class="container">
    <Switch name="test" />
  </div>
</main>

<style lang="scss">
  main {
    display: grid;
    place-items: center;
    min-height: 100vh;
  }

  .container {
    display: flex;
    flex-direction: column;
    gap: 2rem;
    justify-content: center;
    align-items: center;
    background-color: rgb(208, 208, 208);
    height: 300px;
    width: 400px;
    border-radius: 0.5rem;
  }
</style>
