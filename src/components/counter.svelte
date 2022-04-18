<script lang="ts">
  import { Button, Card, CardBody, Input } from 'sveltestrap';
  import { createEventDispatcher } from 'svelte';

  export let id: number;
  export let title = '';
  export let count = 0;
  function incrementCount(): void {
    count += 1;
  }
  function decrementCount(): void {
    if (count > 0) count -= 1;
  }
  function reset(): void {
    count = 0;
  }
  const removeDispatcher = createEventDispatcher<{ remove: { id: number } }>();

  function remove(): void {
    removeDispatcher('remove', { id: id });
  }
</script>

<Card>
  <CardBody>
    <Input style="width: 400px" bind:value={title} placeholder="input counter title" />
    {count}
    <Button color="success" on:click={incrementCount}>+</Button>
    <Button color="danger" on:click={decrementCount}>-</Button>
    <Button color="warning" on:click={reset}>0</Button>
    <Button color="light" on:click={remove}>x</Button>
  </CardBody>
</Card>
