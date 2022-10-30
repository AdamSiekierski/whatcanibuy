<script lang="ts">
  import Money from './components/Money.svelte';
  import { values } from './data/values.json';

  interface ResultItem {
    things: string[];
    from: number;
  }

  let money: number;
  let result: ResultItem[];

  function showResult() {
    result = values.filter(item => item.from <= money).reverse();
  }
</script>

<style type="text/scss">
  .container {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }

  .wrapper {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    text-align: center;
    flex: 1;
  }

  .result {
    max-width: 50ch;
    flex: 1;
  }

  .category {
    .price {
      font-size: 1.25rem;
      position: relative;
      text-align: left;
      color: #ffffff30;
      font-weight: 500;
      display: flex;
      align-items: center;
      gap: 10px;
      margin-bottom: 0;
      margin-top: 1rem;

      .line {
        flex: 1;
        bottom: 0;
        left: 0;
        right: 0;
        border-top: 1px solid #ffffff30;
        border-bottom: 1px solid #ffffff30;
        z-index: -1;
      }
    }

    ul {
      padding-left: 3rem;
      padding-right: 1.5rem;

      li {
        text-align: left;
        padding-left: 1rem;
        color: #ffffff70;
      }
    }

    &:first-of-type {
      .price {
        color: #ffffff;

        .line {
          border-color: #ffffff;
        }
      }

      li {
        color: #ffffff;
      }
    }
  }

  .footer {
    text-align: center;
    padding: 0.5rem;
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

<div class="container">
  <main class="wrapper">
    <div>
      <h1>what can i buy for...</h1>
      <Money bind:value={money} on:input={showResult} />
    </div>
    {#if result}
      <div class="result">
        {#each result as price}
          <div class="category">
            <h2 class="price">
              <span>${price.from}</span>
              <span class="line" />
            </h2>
            <ul>
              {#each price.things.sort() as thing}
                <li>
                  <p>{thing}</p>
                </li>
              {/each}
            </ul>
          </div>
        {/each}
      </div>
    {/if}
    <div />
  </main>
  <footer class="footer">
    made by
    <a href="https://siekierski.ml">adam siekierski</a>
  </footer>
</div>
