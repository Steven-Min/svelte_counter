<script lang="ts">
  import Counter from './Counter.svelte';

  type CounterItem = {
    id: number;
    title: string;
    count: number;
  }

  let counters: CounterItem[] = [
    { id: 1, title: 'new', count: 0 },
  ];
  let total = sumCounters();

  function sumCounters() {
    return counters.reduce((acc, counter) => acc + counter.count, 0);
  }

  function handleCountChange(event) {
    counters = counters.map(counter => {
      if (counter.id === event.detail.id) {
        return { ...counter, count: event.detail.count };
      }
      return counter;
    });
    total = sumCounters();
  }

  function handleRemove(event) {
    counters = counters.filter(counter => counter.id !== event.detail.id);
    total = sumCounters();
  }

  function handleTitleChange(event) {
    counters = counters.map(counter => {
      if (counter.id === event.detail.id) {
        return { ...counter, title: event.detail.title };
      }
      return counter;
    });
  }

</script>

<style>
  .counter-list {
    width: 600px;
    margin-left: auto;
    margin-right: auto;
    text-align: center;
  }

  .counter-append-btn {
    width: 300px;
    margin-left: auto;
    margin-right: auto;
    display: block;
  }
</style>

<div class="counter-list">
  {#each counters as counter}
    <Counter title={counter.title} count={counter.count} id={counter.id} on:countChanged={handleCountChange} on:delete={handleRemove} on:titleChanged={handleTitleChange} />
  {/each}
  <button class="counter-append-btn" on:click={() => counters = [...counters, { id: counters.length + 1, title: `new`, count: 0 }]}>
    Add counter
  </button>
  <div>
    title list: {counters.map(counter => counter.title).join(', ')}
  </div>
  <div>
    Total: {total}
  </div>
</div>
