<script lang="ts">
  // export let name: string;
  import { Styles } from 'sveltestrap';
  import Counter from './components/counter.svelte';

  type TCounter = {
    id: number;
    title: string;
    count: number;
  };

  let counterList: TCounter[] = [{ id: 0, title: '', count: 0 }];
  let nextId = 1;

  function add(): void {
    counterList.concat({ id: nextId, title: '', count: 0 });
    nextId += 1;
  }

  function remove(): void {
    counterList = counterList.slice(1);
  }
</script>

<Styles />

<main>
  <h1>Svelte Counter App</h1>
  {#each counterList as counter}
    <div>
      <Counter {...counter} />
    </div>
  {/each}
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
      max-width: none;
    }
  }
</style>
