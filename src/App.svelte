<script lang="ts">
  // export let name: string;
  import { Styles, Button } from 'sveltestrap';
  import Counter from './components/counter.svelte';
</script>

<Styles />

<main>
  <h1>Svelte Counter App</h1>
  <div>
    <Counter />
  </div>
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
