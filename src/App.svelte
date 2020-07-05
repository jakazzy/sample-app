<script>
	let name= 'Adwoa';
	let beltColor='black'

	const handleClick =()=>{
		beltColor='orange'
	}
	
	const handleInput=(event)=>{
		beltColor= event.target.value
	}
</script>

<main>
	<h1>Hello {name}!</h1>
	<p style="color: {beltColor}">She has {beltColor} belt color</p>
	<button on:click={ handleClick}> update belt color </button>
	<!-- <input type="text" on:input={handleInput} value={beltColor}> -->
	<input type="text" bind:value ={beltColor}>
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