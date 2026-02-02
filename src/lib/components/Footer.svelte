<script lang="ts">
	import logo from '$lib/assets/cashloanslogo.jpg';
	
	const currentYear = new Date().getFullYear();
	
	const quickLinks = [
		{ name: 'Home', href: '/' },
		{ name: 'About', href: '/about' },
		{ name: 'FAQ', href: '/faq' },
		{ name: 'Contact', href: '/contact' },
		{ name: 'Apply Now', href: '/apply' }
	];
	
	const services = [
		{ name: 'Personal Loans', href: '#' },
		{ name: 'Quick Approval', href: '#' },
		{ name: 'Online Application', href: '#' },
		{ name: 'Loan Comparison', href: '#' }
	];
	
	const legalLinks = [
		{ name: 'Terms of Service', href: '#' },
		{ name: 'Privacy Policy', href: '#' },
		{ name: 'Cookie Policy', href: '#' },
		{ name: 'Disclaimer', href: '#' }
	];
	
	const contactInfo = {
		email: 'info@thlakoanengcashloans.co.za',
		phone: '+27 12 345 6789',
		address: 'South Africa'
	};
	
	const socialLinks = [
		{ name: 'Facebook', url: 'https://facebook.com', icon: 'fab fa-facebook-f' },
		{ name: 'Instagram', url: 'https://instagram.com', icon: 'fab fa-instagram' },
		{ name: 'LinkedIn', url: 'https://linkedin.com', icon: 'fab fa-linkedin-in' }
	];
</script>

<footer class="footer">
	<div class="footer-main">
		<div class="footer-container">
			<!-- Company Info -->
			<div class="footer-section">
				<div class="footer-logo">
					<img src={logo} alt="Thlakoaneng Cash Loans Logo" />
				</div>
				<p class="company-description">
					Thlakoaneng Cash Loans helps South Africans find the best loan options from reputable banks and lenders. Compare offers and choose the best fit for your needs.
				</p>
				<div class="social-links">
					{#each socialLinks as link}
						<a href={link.url} target="_blank" rel="noopener noreferrer" aria-label={link.name}>
							<i class={link.icon}></i>
						</a>
					{/each}
				</div>
			</div>

			<!-- Quick Links -->
			<div class="footer-section">
				<h3>Quick Links</h3>
				<ul>
					{#each quickLinks as link}
						<li><a href={link.href}>{link.name}</a></li>
					{/each}
				</ul>
			</div>

			<!-- Services -->
			<div class="footer-section">
				<h3>Our Services</h3>
				<ul>
					{#each services as service}
						<li><a href={service.href}>{service.name}</a></li>
					{/each}
				</ul>
			</div>

			<!-- Contact Info -->
			<div class="footer-section">
				<h3>Contact Us</h3>
				<div class="contact-info">
					<div class="contact-item">
						<i class="fas fa-envelope"></i>
						<span>{contactInfo.email}</span>
					</div>
					<div class="contact-item">
						<i class="fas fa-phone"></i>
						<span>{contactInfo.phone}</span>
					</div>
					<div class="contact-item">
						<i class="fas fa-map-marker-alt"></i>
						<span>{contactInfo.address}</span>
					</div>
				</div>
			</div>
		</div>
	</div>

	<!-- Bottom Bar -->
	<div class="footer-bottom">
		<div class="footer-container">
			<div class="footer-bottom-content">
				<p>&copy; {currentYear} Thlakoaneng Cash Loans. All rights reserved.</p>
				<div class="legal-links">
					{#each legalLinks as link}
						<a href={link.href}>{link.name}</a>
					{/each}
				</div>
			</div>
		</div>
	</div>
</footer>

<style>
	.footer {
		background-color: #ffffff;
		/* color: #1a1a1a; */
		/* margin-top: auto; */
	}

	.footer-main {
		padding: 60px 0 40px;
		/* border-bottom: 1px solid #333; */
	}

	.footer-container {
		max-width: 1200px;
		margin: 0 auto;
		padding: 0 20px;
		display: grid;
		grid-template-columns: 2fr 1fr 1fr 1fr;
		gap: 40px;
	}

	.footer-section h3 {
		/* color: #b; */
		font-family: 'Rubik', sans-serif;
		font-size: 1.2rem;
		margin-bottom: 20px;
		font-weight: 600;
	}

	.footer-logo img {
		height: 50px;
		width: auto;
		margin-bottom: 20px;
	}

	.company-description {
		/* color: #ccc; */
		line-height: 1.6;
		margin-bottom: 25px;
		font-size: 0.95rem;
	}

	.social-links {
		display: flex;
		gap: 15px;
	}

	.social-links a {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 40px;
		height: 40px;
		background-color: #333;
		color: #fff;
		text-decoration: none;
		border-radius: 50%;
		transition: all 0.3s ease;
		font-size: 16px;
	}

	.social-links a:hover {
		background-color: #a30300;
		transform: translateY(-2px);
	}

	.footer-section ul {
		list-style: none;
		padding: 0;
		margin: 0;
	}

	.footer-section ul li {
		margin-bottom: 12px;
	}

	.footer-section ul li a {
		color: black;
		text-decoration: none;
		transition: color 0.3s ease;
		font-size: 0.95rem;
	}

	.footer-section ul li a:hover {
		color: #ffd900;
	}

	.contact-info {
		display: flex;
		flex-direction: column;
		gap: 15px;
	}

	.contact-item {
		display: flex;
		align-items: center;
		gap: 12px;
		color: black;
		font-size: 0.95rem;
	}

	.contact-item i {
		color: #a30300;
		width: 20px;
		text-align: center;
	}

	.footer-bottom {
		padding: 25px 0;
		background-color: #0d0d0d;
	}

	.footer-bottom-content {
		display: flex;
		justify-content: space-between;
		align-items: center;
		flex-wrap: wrap;
		gap: 20px;
	}

	.footer-bottom p {
		color: #999;
		margin: 0;
		font-size: 0.9rem;
	}

	.legal-links {
		display: flex;
		gap: 20px;
		flex-wrap: wrap;
	}

	.legal-links a {
		color: #999;
		text-decoration: none;
		font-size: 0.9rem;
		transition: color 0.3s ease;
	}

	.legal-links a:hover {
		color: #ffd900;
	}

	/* Responsive Design */
	@media (max-width: 1024px) {
		.footer-container {
			grid-template-columns: 1fr 1fr;
			gap: 30px;
		}
	}

	@media (max-width: 768px) {
		.footer-container {
			grid-template-columns: 1fr;
			gap: 30px;
			text-align: center;
		}

		.social-links {
			justify-content: center;
		}

		.footer-bottom-content {
			flex-direction: column;
			text-align: center;
		}

		.legal-links {
			justify-content: center;
		}
	}

	@media (max-width: 480px) {
		.footer-main {
			padding: 40px 0 30px;
		}

		.footer-container {
			padding: 0 15px;
		}

		.footer-section h3 {
			font-size: 1.1rem;
		}

		.company-description {
			font-size: 0.9rem;
		}

		.legal-links {
			flex-direction: column;
			gap: 10px;
			align-items: center;
		}
	}
</style>