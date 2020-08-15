<script lang="ts">
  import Money from './components/Money.svelte';

  let money: number;
</script>

<style type="text/scss">
  .wrapper {
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
</style>

<main class="wrapper">
  <h1>what can i buy for...</h1>
  <Money bind:value={money} on:submit={() => console.log('dupa')} />
</main>
