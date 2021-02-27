<script>
	import userApi from './users-api';
	import UserCard from './components/UserCard.svelte';
	export let name;

	let users = [];

	async function getUsers() {
		users = await userApi.getUsers();
	}

	getUsers();


</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	{#each users as user}
		<UserCard {user} />
	{/each}
	
</main>

















<style  global lang="postcss">
	/* only apply purgecss on utilities, per Tailwind docs */
  /* purgecss start ignore */
  @tailwind base;
  @tailwind components;
  /* purgecss end ignore */

  @tailwind utilities;
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