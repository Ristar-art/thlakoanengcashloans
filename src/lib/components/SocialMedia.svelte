<script lang="ts">
	// Social media links - replace with actual URLs
	const socialLinks = [
		{ name: 'Facebook', url: 'https://facebook.com', icon: 'fab fa-facebook-f' },
		{ name: 'Instagram', url: 'https://instagram.com', icon: 'fab fa-instagram' },
		{ name: 'Envelope', url: 'https://linkedin.com', icon: 'fas fa-envelope' }
	];
</script>

<div class="social-media">
	{#each socialLinks as link}
		<a href={link.url} target="_blank" rel="noopener noreferrer" aria-label={link.name}>
			<i class={link.icon}></i>
		</a>
	{/each}
</div>

<style>
	.social-media {
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		display: flex;
		justify-content: center;
		gap: 20px;
		padding: 10px 0;
		background-color: #fff;
		border-bottom: 1px solid #e9ecef;
		z-index: 1001;
	}

	.social-media a {
		text-decoration: none;
		font-size: 24px;
		color: #6c757d;
		transition: color 0.3s ease;
	}

	.social-media a:hover {
		color: #a30300;
	}
</style>