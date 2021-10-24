<script>
	 let name = "Joe"; //have a variable name that can be set from outside the component
	 let age = 58;

	 function incAge()
	 {
		 age += 1;
	 }
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>My age is {age}</p>
	<button on:click="{incAge}">Change Age</button> 
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