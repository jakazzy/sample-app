<script>
import Modal from './Modal.svelte'
import AddPersonForm from './AddPersonForm.svelte'

let showModal= false
let people=[
	{name: 'yoshi', beltColor: 'black', age: 25, id: 1},
	{name: 'mario', beltColor: 'orange', age: 45, id: 2},
	{name: 'luigi', beltColor: 'brown', age: 35, id: 3}
	]

const handleClick=(id)=>{
		people =people.filter( person => person.id !== id)
	}
const toggleModal=()=>{
	showModal = !showModal
}

const addPerson =(event)=>{
	const person= event.detail
	people = [person, ...people]
	showModal=false
}
</script>


<Modal  isPromo={true} {showModal} on:click={toggleModal}>
	<AddPersonForm on:addPerson={addPerson} />
</Modal>
<main>
	<button on:click={toggleModal}>Open Modal</button>
	{ #each people as person (person.id)}
	<div>
		<h4>{person.name}</h4>
		{#if person.beltColor==='black'}
		<p> <strong>Master Ninja</strong> </p>
		{/if}
		<p> {person.age} years old, {person.beltColor} belt. </p>
		{ #if person.skills}
			<p>Skills: </p>
			<ul>
				{ #each person.skills as skill }
				<li>{skill}</li>
				{/each}
			</ul>
		{ /if }
		
		<button on:click={()=>handleClick(person.id)}> delete</button>
	</div>
	{ :else }
	<p> There are no people to show...</p>
	{ /each}
	
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	/* h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	} */

	ul{margin: 0}
	li{
		display: inline-block;
		margin-right: 5px
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>