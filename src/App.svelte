<script lang="ts">
  let value = '';
</script>

<style type="text/scss">
  .wrapper {
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .input {
    background: none;
    color: white;
    border: 1px solid #222;
    border-radius: 5px;
    padding: 10px;
    outline: none;
    transition: box-shadow 0.5s ease;
    font-family: inherit;

    &:focus {
      box-shadow: 0px 0px 0px 3px orangered;
    }
  }
</style>

<main class="wrapper">
  <h1>what can i buy for...</h1>
  <input type="text" {value} class="input" placeholder="monni" />
</main>
