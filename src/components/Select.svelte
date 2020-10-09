<!-- src/components/Select.svelte -->
<script>
  export let value;
  export let options;
  export let label;
  export let id;
</script>

<label for={id}>{label}</label>
<select bind:value {id}>
  {#each options as option}
    <option value={option.value}>{option.label}</option>
  {/each}
</select>
