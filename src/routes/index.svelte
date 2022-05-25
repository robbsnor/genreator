<script lang="ts">
	import Header from './../components/header.svelte';
	import { Spotify } from './../service/spotify.service.ts';
    import Album from '../components/album.svelte';
</script>
<Header></Header>

<Album title="yo"></Album>
<Album title="yos"></Album>

<style lang="scss" global>
    @import '../style/app';
</style>