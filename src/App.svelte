<script lang="ts">
  import { Button, Styles } from 'sveltestrap';
  import Counter from './components/counter.svelte';

  type TCounter = {
    id: number;
    title: string;
    count: number;
  };

  let counterList: TCounter[] = [{ id: 0, title: 'new counter', count: 0 }];
  let nextId = 1;

  function add(): void {
    counterList = counterList.concat({ id: nextId, title: 'new counter', count: undefined });
    nextId += 1;
  }

  function remove(event: CustomEvent<{ id: number }>): void {
    counterList = counterList.filter((counterList) => counterList.id != event.detail.id);
  }

  $: sumOfCounter = counterList.reduce((sum, curr) => sum + curr.count, 0);

  $: titleList = counterList.map((counter) => counter.title).join();
</script>

<Styles />
<main>
  <h1>Svelte Counter App</h1>
  {#each counterList as counter (counter.id)}
    <div>
      <Counter id={counter.id} on:remove={remove} bind:title={counter.title} bind:count={counter.count} />
    </div>
  {/each}

  <Button block color="info" on:click={add}>new counter</Button>
  <p>
    title list: {titleList}
  </p>
  <p>sum of count: {sumOfCounter}</p>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: 1000px;
    }
  }
</style>
