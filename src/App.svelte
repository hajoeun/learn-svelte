<script>
	import axios from 'axios';
	import { onMount } from 'svelte';

	let articles = [];
	onMount(async () => {
		const { data } = await axios.get('https://conduit.productionready.io/api/articles?limit=10&offset=0');
		articles = data.articles;
	});

	export let name;
</script>

<main>
<h1>{name}</h1>
<ul>
  {#each articles as article}
		<li>{article.title}</li>
	{/each}
</ul>
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
		font-size: 24px;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
