<script>
	import Album from './components/album.svelte'
	export let name;

	export let albums = [
		{
			title: 'title 1',
			image: 'img.png'
		},
		{
			title: 'title 2',
			image: 'img.png'
		},
		{
			title: 'title 3',
			image: 'img.png'
		},
	];

	 function addAlbum() {
		albums = [...albums, {title: 'new one wow', image: 'wow.jpg'}]
	}

</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>

	{#each albums as album, i}
		<Album {...albums[i]}></Album>
	{/each}

	<button on:click={addAlbum}>add Ablum</button>

</main>

<style>
</style>