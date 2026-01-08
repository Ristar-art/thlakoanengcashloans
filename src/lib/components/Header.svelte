<script lang="ts">
	import logo from '$lib/assets/cashloanslogo.jpg';
	let menuOpen = false;
</script>

<header class="fixed-header">
	<div class="header-content">
		<div class="logo">
			<img src={logo} alt="Thlakoaneng Cash Loans Logo" />
		</div>
		<button class="hamburger" on:click={() => menuOpen = !menuOpen} aria-label="Toggle menu">
			<span></span>
			<span></span>
			<span></span>
		</button>
		<nav class:mobile-menu={menuOpen}>
			<ul>
				<li><a href="/">Home</a></li>
				<li><a href="/about">About</a></li>
				<li><a href="/faq">FAQ</a></li>
				<li><a href="/contact">Contact</a></li>
			</ul>
		</nav>
        
            
        <button class="apply-button">
            <a href="/apply">Apply</a>
        </button>

	</div>
</header>

<style>
	.fixed-header {
		position: fixed;
		top: 44px;
		left: 0;
		right: 0;
		background-color: #fff;
		/* box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); */
		z-index: 1000;
		padding: 10px 20px;
	}

	.header-content {
		display: flex;
		justify-content: space-between;
		align-items: center;
		max-width: 1200px;
		margin: 0 auto;
	}

	.logo img {
		height: 60px;
		width: auto;
	}

	nav ul {
		display: flex;
		list-style: none;
		margin: 0;
		padding: 0;
		gap: 30px;
	}

	nav a {
		text-decoration: none;
		color: #333;
		font-weight: 500;
		transition: color 0.3s ease;
	}

	nav a:hover {
		color: #a30300;
	}


	.hamburger {
		display: none;
		flex-direction: column;
		background: none;
		border: none;
		cursor: pointer;
		padding: 10px;
	}

	.hamburger span {
		width: 25px;
		height: 3px;
		background-color: #333;
		margin: 3px 0;
		transition: 0.3s;
	}

	.mobile-menu {
		display: none;
	}

	@media (max-width: 768px) {
		.hamburger {
			display: flex;
		}
		nav {
			display: none;
		}
		.mobile-menu {
			display: block;
			position: absolute;
			top: 100%;
			left: 0;
			right: 0;
			background-color: #fff;
			box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
			padding: 10px 0;
		}
		.mobile-menu ul {
			flex-direction: column;
			gap: 0;
		}
		.mobile-menu li {
			padding: 10px 20px;
		}
		.mobile-menu a {
			color: #333;
		}
	}

	/* Add padding to body to prevent content from being hidden behind fixed header */
	:global(body) {
		padding-top: 120px;
	}
</style>