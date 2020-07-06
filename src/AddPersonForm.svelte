<script>
    let name;
    let beltColor;
    let age;

    const handleSubmit=()=>{}
</script>

<h3>Add a new person</h3>
<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="name" bind:value={name}>
    <input type="text" placeholder="belt color" bind:value={beltColor}>
    <input type="number" placeholder="age" bind:value={age}>
    <button> Add Person</button>
</form>

<style></style>