<script>
  import Input from "./Input.svelte";
  import Select from "./Select.svelte";

  export let onSubmit;
  export let fields;

  // Convert fields from [ { name: 'name', value: 'Value' } ] to { name : Value } which is more useful when submitting a form
  const fieldsToObject = (fields) =>
    fields.reduce((p, c) => ({ ...p, [c.name]: c.value }), {});

  // When submitting, turn our fields representation into a JSON body
  const handleSubmit = () => onSubmit(fieldsToObject(fields));
</script>

<style>
  :global(input, select) {
    margin: 5px;
  }
</style>

<!-- When submitting, prevent the default action which would result in a refreshed page -->
<form on:submit|preventDefault={() => handleSubmit(fields)}>
    <!-- Loop the fields and render the correct representation based on field.type -->
    {#each fields as field}
        {#if field.type === 'Input'}
            <Input bind:value={field.value} label={field.label} placeholder={field.placeholder} />
        {:else if field.type === "Select"}
            <Select bind:value={field.value} label={field.label} options={field.options}/>
        {/if}
    {/each}
    <button type="submit">Submit</button>
</form>
