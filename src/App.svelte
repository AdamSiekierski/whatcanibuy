<script lang="ts">
  import Money from './components/Money.svelte';
  import { values } from './data/values.json';

  interface ResultItem {
    things: string[];
    from: number;
  }

  let money: number;
  let result: ResultItem;

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
    justify-content: space-between;
    align-items: center;
    text-align: center;
  }

  .footer {
    text-align: center;
    padding: 2px;
    font-size: 0.8em;

    a {
      color: white;
      text-decoration: none;
      transition: color 0.3s ease;

      &:hover {
        color: orangered;
      }
    }
  }
</style>

<main class="wrapper">
  <div>
    <h1>what can i buy for...</h1>
    <Money bind:value={money} on:input={showResult} />
  </div>
  {#if result}
    <div class="result">
      {#each result.things as thing}
        <p>{thing}</p>
      {/each}
    </div>
  {/if}
  <div />
</main>
<footer class="footer">
  made by
  <a href="https://siekierski.ml">adam siekierski</a>
</footer>
