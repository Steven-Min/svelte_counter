<script lang="ts">
  import { createEventDispatcher } from 'svelte';
  import Button from './Button.svelte';

  const dispatch = createEventDispatcher();

  export let title: string = 'Counter Title';
  export let count: number = 0;
  export let id: number = 1;


  // これらの関数は以前と変わらず定義します
  function increment() {
    count += 1;
    dispatch('countChanged', { id, count });
  }

  function decrement() {
    // マイナスにならないように
    if (count > 0) {
        count -= 1;
    }
    dispatch('countChanged', { id, count });
  }

  function reset() {
    count = 0;
    dispatch('countChanged', { id, count });
  }

  function remove() {
    dispatch('delete', { id });
  }

  function changeTitle(event) {
    title = event.target.value;
    dispatch('titleChanged', { id, title });
  }
</script>

<style>
  /* Counter.svelte の <style> タグ内、またはグローバルスタイルシートに追加 */
  .danger {
    background-color: #dc3545; /* 赤色の背景 */
    color: white; /* 白色のテキスト */
  }

  .danger:hover {
    background-color: #c82333; /* ホバー時の色 */
  }

  .counter-button {
    display: flex;
    align-items: center;
    margin: 10px;
    padding: 10px;
    border-radius: 5px;
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
  }

  input {
    margin-right: 10px;
    margin-bottom: 0;
  }

  .count-number {
    margin-right: 10px;
  }
</style>

<div class="counter-button">
  <input type="text" bind:value={title} on:change={changeTitle} />
  <div class="count-number">Count: {count}</div>
  <div>
    <Button text="+" onClick={increment} />
    <Button text="-" onClick={decrement} />
    <Button text="Reset" onClick={reset} />
    <Button text="Remove" onClick={remove} className="danger" />
  </div>
</div>
