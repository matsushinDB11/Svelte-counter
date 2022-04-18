<script lang="ts">
  import { Button, Styles } from 'sveltestrap';
  import Counter from './components/counter.svelte';

  // TODO この型いる？
  type TCounter = {
    id: number;
  };

  let counterList: TCounter[] = [{ id: 0 }];
  let nextId = 1;

  function add(): void {
    counterList = counterList.concat({ id: nextId });
    nextId += 1;
  }

  function remove(event: CustomEvent<{ id: number }>): void {
    counterList = counterList.filter((counterList) => counterList.id != event.detail.id);
  }
</script>

<Styles />

<main>
  <h1>Svelte Counter App</h1>
  {#each counterList as counter (counter.id)}
    <div>
      <Counter id={counter.id} on:remove={remove} />
    </div>
  {/each}

  <Button block color="info" on:click={add}>new counter</Button>
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
