<script lang="ts">
  import { createEventDispatcher } from 'svelte';

  export let value: number;

  let focused = false;
  const dispatch = createEventDispatcher();

  const onFocusChange = () => (focused = !focused);
  const onInput = () => dispatch('input');
</script>

<style lang="scss">
  .money {
    border: 1px solid #222;
    border-radius: 5px;
    transition: box-shadow 0.5s ease, color 0.3s ease;
    box-shadow: 0px 0px 0px 0px orangered;
    font-size: 0.8em;
    text-align: left;
    max-width: 300px;
    margin: 0 auto;
    display: flex;
    align-items: center;
    padding-left: 10px;

    &--focused {
      box-shadow: 0px 0px 0px 3px orangered;
    }
  }

  .money__input {
    background: none;
    color: white;
    padding: 0;
    outline: none;
    font-family: inherit;
    position: relative;
    border: none;
    padding: 10px;
    -moz-appearance: textfield;
    flex: 1;

    &::-webkit-input-placeholder {
      color: gray;
      opacity: 1;
    }
    &::-moz-placeholder {
      color: gray;
      opacity: 1;
    }
    &:-ms-input-placeholder {
      color: gray;
      opacity: 1;
    }
    &:-moz-placeholder {
      color: gray;
      opacity: 1;
    }
    &::-webkit-inner-spin-button {
      -webkit-appearance: none;
      margin: 0;
    }
    &::-webkit-outer-spin-button {
      -webkit-appearance: none;
      margin: 0;
    }
  }
</style>

<div class="money {focused && 'money--focused'}" style="color: {value ? 'white' : 'gray'}">
  $
  <input
    type="number"
    bind:value
    class="money__input"
    placeholder="monni"
    on:focus={onFocusChange}
    on:blur={onFocusChange}
    on:input={onInput} />
</div>
