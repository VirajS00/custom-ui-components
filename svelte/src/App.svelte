<script lang="ts">
  import CheckBox from './components/CheckBox.svelte';
</script>

<main>
  <div class="container">
    <CheckBox name="test" label="test" />
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
    height: 300px;
    width: 400px;
    border-radius: 0.5rem;
  }
</style>
