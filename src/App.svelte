<script>

	import ContactCard from './ContactCard.svelte'

	let userName = 'Mel'
	let userImage = ''
	let jobTitle = ''
	let description = ''
	let formState = 'empty'

	// let password = ''
	// let passwordState = 'passed'
	// let passwordArray = []

	let createdContacts = []

	function addContact() {
		if (userName.trim().length === 0 ||
			jobTitle.trim().length === 0 ||
			userImage.trim().length === 0 ||
			description.trim().length === 0) {
				formState = 'invalid'
				return
			}
		createdContacts = [...createdContacts, { id: Math.random(), userName, jobTitle, userImage, description }]
		formState = 'done'
	}

	// function addPassword() {
	// 	if (password.length < 5) {
	// 		passwordState = 'short'
	// 		return
	// 	}
	// 	if (password.length > 10) {
	// 		passwordState = 'long'
	// 		return
	// 	}
	// 	passwordArray = [...passwordArray, password ]
	// 	passwordState = 'passed'
	// }

	function deleteFirst() {
		createdContacts = createdContacts.slice(1)
	}

	function deleteLast() {
		createdContacts = createdContacts.slice(0, -1)
	}

	// function deleteFirstPassword() {
	// 	passwordArray = passwordArray.slice(1)
	// }

	// function deleteLastPassword() {
	// 	passwordArray = passwordArray.slice(0, -1)
	// }

</script>

<style>
	#form {
		width: 30rem;
		max-width: 100%;
	}
</style>


<!-- <div id='form'>
	<div class="form-control">
		<label for="password">Password</label>
		<input type='text' bind:value={ password } id='password' />
	</div>
	<button on:click={ addPassword }>Add Password</button>
	<button on:click={ deleteFirstPassword }>(+) First Password</button>
	<button on:click={ deleteLastPassword }>(-) Last Password</button>

	{#if passwordState === 'short'}
		<p>Too short</p>
	{:else if passwordState === 'long'}
		<p>Too long</p>
	{/if}

	{#each passwordArray as singleArray, i}
	<ul>
		<li>{ singleArray }</li>
	</ul>
	{:else}
		<p>Please create a password!</p>
	{/each}
</div> -->

<div id="form">
	<div class="form-control">
		<label for="userName">User Name</label>
		<input type="text" bind:value={ userName } id="userName" />
	</div>
	<div class="form-control">
		<label for="jobTitle">Job Title</label>
		<input type="text" bind:value={ jobTitle } id="jobTitle" />
	</div>
	<div class="form-control">
		<label for="image">Image URL</label>
		<input type="text" bind:value={ userImage } id="image" />
	</div>
	<div class="form-control">
		<label for="desc">Description</label>
		<textarea rows="3" bind:value={ description } id="desc" />
	</div>
</div>

<button on:click={ addContact }>Add Contact Card</button>
<button on:click={ deleteFirst }>Delete First</button>
<button on:click={ deleteLast }>Delete Last</button>
  

{#if formState === 'invalid'}
	<p>Invalid Input</p>
{:else}
	<p>Please enter some data and hit the button</p>
{/if}

{#each createdContacts as contact, i (contact.id)}
<h2># { i + 1 }</h2>
<ContactCard
	userName={ contact.userName }
	userImage={ contact.userImage } 
	jobTitle={ contact.jobTitle }
	description={ contact.description } />
{:else}
	<p>Please start adding some contact, we found none!</p>
{/each}
