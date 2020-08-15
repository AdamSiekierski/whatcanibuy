<script lang="ts">
  import { createEventDispatcher } from 'svelte';
  import debounce from 'lodash.debounce';

  export let value: number;

  let focused = false;
  const dispatch = createEventDispatcher();

  const onChange = () => (focused = !focused);
  const onSubmit = debounce(() => value && dispatch('submit'), 2500);
</script>

<style lang="scss">
  .money {
    border: 1px solid #222;
    border-radius: 5px;
    transition: box-shadow 0.5s ease, color 0.3s ease;
    box-shadow: 0px 0px 0px 0px orangered;
    padding: 10px;
    font-size: 0.8em;

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
    margin-left: 1ch;
    -moz-appearance: textfield;

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
    on:focus={onChange}
    on:blur={onChange}
    on:input={onSubmit} />
</div>
