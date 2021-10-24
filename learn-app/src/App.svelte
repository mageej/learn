<script>
	import ContactCard from './ContactCard.svelte';

	 let name = "Joseph"; //have a variable name that can be set from outside the component
	 let age = 58;
	 let jobTitle;
	 let jobDescription;
	 let imgURL;

	 //labelled statements is the base, but svelte uses this for dynamic reactive expressions
	 // so whenever name (dependencies on the line) changes the $: expression will be run
	$: uppercaseName = name.toUpperCase();

	$: console.log(name);

	$: if (name === 'Kati') { age = 58; }

	 function incAge()
	 {
		 age += 1;
	 }

	 function changeName()
	 {
		 name = 'Kati';
		 //will automatically run the $: expression
	 }
	 //curly braces is the core concept

	 //event is passed by defeult for events
	 function nameInput (event) {
         const enteredValue = event.target.value;
		 name = enteredValue;
	 }
</script>


<main>
	<h1>Hello {uppercaseName}</h1>
	<p>My age is {age}</p>
	<button on:click="{incAge}">Change Age</button> 
	<!-- <button on:click="{changeName}">Change Name</button>  -->
	<!-- <input type='Text' value="{name}" on:input="{nameInput}"/> -->
	<input type='Text' bind:value="{name}" />
	<input type='Text' aria-label="Job Title" bind:value="{jobTitle}" />
	<input type='Text' aria-label="Job Description" bind:value="{jobDescription}" />

	<ContactCard userName="{name}" jobTitle={jobTitle} jobDescription={jobDescription} />
</main>

<!-- note these styles are only scoped to this component -->
<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>