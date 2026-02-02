<script lang="ts">
	import favicon from '$lib/assets/cashloanslogo.jpg';
	import Header from '$lib/components/Header.svelte';
	import SocialMedia from '$lib/components/SocialMedia.svelte';
	import '@fontsource/rubik';
	import '@fontsource/roboto';
	import '../global.css';
  import Footer from '$lib/components/Footer.svelte';
	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
	<script src="https://www.google.com/recaptcha/api.js" async defer></script>
</svelte:head>
<SocialMedia />
<Header/>
<div style="background-color:#eddd9f; min-height: 100vh; display: flex; flex-direction: column;">
	{@render children()}
</div>
<Footer/>

<style>
	:global(body) {
		font-family: 'Roboto', sans-serif;
	}

	:global(h1), :global(h2), :global(h3), :global(h4), :global(h5), :global(h6) {
		font-family: 'Rubik', sans-serif;
	}
	
</style>