<script>
  import Form from "./components/Form.svelte";

  //   Our field representation, let's us easily specify several inputs
  let fields = [
    {
      name: "firstName",
      type: "Input",
      value: "",
      placeholder: "Enter first name...",
      label: "First name",
    },
    {
      name: "lastName",
      type: "Input",
      value: "",
      placeholder: "Enter last name...",
      label: "Last name",
    },
  ];

  let result = {};
</script>

<Form
  onSubmit={(body) => {
    result = body;
  }}
  {fields} />

<!-- Show the current state of our Form -->
<pre><code>{JSON.stringify(result, 0, 2)}</code></pre>
