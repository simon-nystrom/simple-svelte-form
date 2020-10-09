<script>
  import Input from "./components/Input.svelte";
  let value = "Initial input";
</script>

<main>
  <Input
    bind:value
    name="name"
    label="Name"
    id="name"
    placeholder="Enter name..." />
</main>
