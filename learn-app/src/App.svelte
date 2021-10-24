<script>
	import ContactCard from "./ContactCard.svelte";
	import Passwords from "./PasswordsAssignment.svelte";

	let name = "Max";
	let title = "";
	let image = "";
	let description = "";
	let formState = "empty";

	let createdContacts = [];

	function addContact() {
		if (name.trim().length === 0 || title.trim().length === 0) {
			formState = "invalid";
			return;
		}

		//for arrays they need to percived as reactive so suse the spread construct ...
		createdContacts = [
			...createdContacts,
			{
				id: Math.random(),
				name: name,
				jobTitle: title,
				imageUrl: image,
				desc: description,
			},
		];
		formState = "done";
	}

	function delFirst() {
		createdContacts = createdContacts.slice(1);
	}

	function delLast() {
		createdContacts = createdContacts.slice(0, -1);
	}
</script>

<div id="form">
	<div class="form-control">
		<label for="userName">User Name</label>
		<input type="text" bind:value={name} id="userName" />
	</div>
	<div class="form-control">
		<label for="jobTitle">Job Title</label>
		<input type="text" bind:value={title} id="jobTitle" />
	</div>
	<div class="form-control">
		<label for="image">Image URL</label>
		<input type="text" bind:value={image} id="image" />
	</div>
	<div class="form-control">
		<label for="desc">Description</label>
		<textarea rows="3" bind:value={description} id="desc" />
	</div>
</div>

<button on:click={addContact}>Add Contact Card</button>
<button on:click={delFirst}>Delete First</button>
<button on:click={delLast}>Delete Last</button>

{#if formState === "invalid"}
	<p>Invalid</p>
{:else}
	<p>enter some data</p>
{/if}

<!-- give lists a unique id so that svelte can correctly manage them -->
{#each createdContacts as contact, i (contact.id)}
	<h2>#{i}</h2>
	<ContactCard
		userName={contact.name}
		jobTitle={contact.jobTitle}
		description={contact.desc}
		userImage={contact.imageUrl}
	/>
{:else}
	<p>please start adding some contacts</p>
{/each}

<Passwords />

<style>
	#form {
		width: 30rem;
		max-width: 100%;
	}
</style>
