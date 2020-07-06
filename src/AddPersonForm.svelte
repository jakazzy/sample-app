<script>
import { createEventDispatcher } from 'svelte'
    let name;
    let beltColor;
    let age;
    let skills=[]
    let dispatch = createEventDispatcher()

    const handleSubmit=()=>{
       const person={ name, age, beltColor, skills, id: Math.random()}
        dispatch('addPerson', person)
    }
</script>

<h3>Add a new person</h3>
<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="name" bind:value={name}>
    <input type="number" placeholder="age" bind:value={age}>
    <label>Skills</label>
    <input type="checkbox" bind:group={skills} value="fighting"> Fighting<br>
    <input type="checkbox" bind:group={skills} value="sneaking"> Sneaking<br>
    <input type="checkbox" bind:group={skills} value="running"> Running<br>

    <label>Belt Color:</label>
    <select bind:value={beltColor}>
        <option value="black">black</option>
        <option value="orange">orange</option>
        <option value="brown">brown</option>
        <option value="white">white</option>
    </select>
    <button> Add Person</button>
</form>

<style></style>