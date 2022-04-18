<script lang="ts">
  import { Button, Card, CardBody, Input } from 'sveltestrap';

  let count = 0;
</script>

<Card>
  <CardBody>
    <Input style="width: 400px" />
    {count}

    <Button color="success" on:click={(count += 1)}>+</Button>
    <Button color="danger">-</Button>
    <Button color="warning">0</Button>
  </CardBody>
</Card>
