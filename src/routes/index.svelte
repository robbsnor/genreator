<script lang="ts">
    import { onMount } from 'svelte';
	import Header from './../components/header.svelte';
	import { Spotify } from './../service/spotify.service.ts';
    import Album from '../components/album.svelte';

    var client_id = '4acb2c2beed54527aa5851b75467fe86';
    // var redirect_uri = 'http://localhost:3000/';
    var redirect_uri = 'http://localhost:3000/';
    var scope = 'user-read-private user-read-email';
    var url = 'https://accounts.spotify.com/authorize';
    url += '?response_type=token';
    url += '&client_id=' + encodeURIComponent(client_id);
    url += '&scope=' + encodeURIComponent(scope);
    url += '&redirect_uri=' + encodeURIComponent(redirect_uri);

    function getHashValue(key) {
        const matches = location.hash.match(new RegExp(key + '=([^&]*)'));
        return matches ? matches[1] : null;
    }

    onMount(() => {
        // const redirectUrl = window.location.origin;
        const accessToken = getHashValue('access_token');
        redirect_uri = window.location.origin;

        fetch('https://api.spotify.com/v1/tracks/2TpxZ7JUBn3uw46aR7qd6V', {
            headers: {
                'Authorization': `Bearer ${accessToken}`
            }
        })
        .then(res => res.json())
        .then(res => {
            console.log(res);
        })
    });

</script>

<div>
    <a href="{ url }">Login</a>
</div>

<style lang="scss" global>
    @import '../style/app';
</style>