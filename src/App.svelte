<script lang="ts">
  import Money from './components/Money.svelte';
  import { values } from './data/values.json';

  interface ResultItem {
    value: string;
    from: number;
  }

  let money: number;
  let result: ResultItem = values[0];

  function showResult() {
    result = values.reduce((previousValue, currentValue) =>
      money >= currentValue.from ? currentValue : previousValue,
    );
  }
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
  <Money bind:value={money} on:input={showResult} />
  {#if result}
    <p class="result">{result.value}</p>
  {/if}
</main>
