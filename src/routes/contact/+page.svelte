<script>
	import hero from '$lib/assets/businesswoman.jpg';
	
	let formData = {
		name: '',
		email: '',
		phone: '',
		message: ''
	};
	
	let isSubmitting = false;
	let submitMessage = '';
	
	function handleSubmit() {
		isSubmitting = true;
		
		// Simulate form submission
		setTimeout(() => {
			submitMessage = 'Thank you for your message. We will get back to you soon!';
			isSubmitting = false;
			
			// Reset form
			formData = {
				name: '',
				email: '',
				phone: '',
				message: ''
			};
			
			// Clear message after 5 seconds
			setTimeout(() => {
				submitMessage = '';
			}, 5000);
		}, 1500);
	}
	
	function handleInputChange(field, value) {
		formData[field] = value;
	}
</script>

<section style="width: 100%; height:60vh; background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url({hero}); background-size:cover; background-position:center; display: flex; justify-content:center; align-items:center;">
	<h1 style="color: #ffd900;">Contact Us</h1>
</section>

<section style="width: 1200px; max-width: 1200px; margin: 100px auto; padding: 0 20px;">
	<div class="contact-container">
		<div class="contact-info">
			<h2>Get in Touch</h2>
			<p>We're here to help you with your loan needs. Reach out to us through any of the following channels:</p>
			
			<div class="contact-details">
				<div class="contact-item">
					<div class="contact-icon">
						<i class="fas fa-phone"></i>
					</div>
					<div class="contact-text">
						<h3>Phone</h3>
						<p>076 079 6043</p>
						<p>061 337 0062</p>
					</div>
				</div>
				
				<div class="contact-item">
					<div class="contact-icon">
						<i class="fas fa-envelope"></i>
					</div>
					<div class="contact-text">
						<h3>Email</h3>
						<p>info@thlakoanengcashloans.co.za</p>
					</div>
				</div>
				
				<div class="contact-item">
					<div class="contact-icon">
						<i class="fas fa-clock"></i>
					</div>
					<div class="contact-text">
						<h3>Open Hours</h3>
						<p>Monday to Friday</p>
						<p>8:00 - 17:00</p>
					</div>
				</div>
			</div>
		</div>
		
		<div class="contact-form">
			<h2>Send us a Message</h2>
			
			{#if submitMessage}
				<div class="success-message">
					{submitMessage}
				</div>
			{/if}
			
			<form on:submit|preventDefault={handleSubmit}>
				<div class="form-group">
					<label for="name">Full Name *</label>
					<input 
						type="text" 
						id="name" 
						name="name" 
						required
						bind:value={formData.name}
						placeholder="Enter your full name"
					/>
				</div>
				
				<div class="form-group">
					<label for="email">Email Address *</label>
					<input 
						type="email" 
						id="email" 
						name="email" 
						required
						bind:value={formData.email}
						placeholder="Enter your email address"
					/>
				</div>
				
				<div class="form-group">
					<label for="phone">Phone Number</label>
					<input 
						type="tel" 
						id="phone" 
						name="phone"
						bind:value={formData.phone}
						placeholder="Enter your phone number"
					/>
				</div>
				
				<div class="form-group">
					<label for="message">Message *</label>
					<textarea 
						id="message" 
						name="message" 
						required
						bind:value={formData.message}
						placeholder="Tell us how we can help you..."
						rows="5"
					></textarea>
				</div>
				
				<button 
					type="submit" 
					class="apply-button submit-button"
					disabled={isSubmitting}
				>
					{#if isSubmitting}
						<span class="spinner"></span>
						Sending...
					{:else}
						Send Message
					{/if}
				</button>
			</form>
		</div>
	</div>
</section>

<style>
	.contact-container {
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: 4rem;
		margin-bottom: 4rem;
        
	}
	
	.contact-info h2,
	.contact-form h2 {
		font-family: 'Rubik', sans-serif;
		font-size: 2rem;
		color: #333;
		margin-bottom: 1rem;
	}
	
	.contact-info p {
		color: #666;
		line-height: 1.6;
		margin-bottom: 2rem;
	}
	
	.contact-details {
		display: flex;
		flex-direction: column;
		gap: 1.5rem;
	}
	
	.contact-item {
		display: flex;
		align-items: flex-start;
		gap: 1rem;
	}
	
	.contact-icon {
		width: 50px;
		height: 50px;
		background-color: #a30300;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
		color: #fff;
		font-size: 1.2rem;
		flex-shrink: 0;
	}
	
	.contact-text h3 {
		font-family: 'Rubik', sans-serif;
		font-size: 1.1rem;
		color: #333;
		margin-bottom: 0.5rem;
	}
	
	.contact-text p {
		color: #666;
		margin-bottom: 0.25rem;
		line-height: 1.5;
	}
	
	.contact-form {
        background: rgba(255, 255, 255, 0.9);
		padding: 2rem;
		border-radius: 8px;
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
	}
	
	.form-group {
		margin-bottom: 1.5rem;
	}
	
	.form-group label {
		display: block;
		font-family: 'Rubik', sans-serif;
		font-weight: 600;
		color: #333;
		margin-bottom: 0.5rem;
	}
	
	.form-group input,
	.form-group textarea {
		width: 100%;
		padding: 0.75rem;
		border: 1px solid #e0e0e0;
		border-radius: 5px;
		font-family: 'Roboto', sans-serif;
		/* font-size: 1rem; */
		transition: border-color 0.3s ease;
		box-sizing: border-box;
	}
	
	.form-group input:focus,
	.form-group textarea:focus {
		outline: none;
		border-color: #a30300;
	}
	
	.form-group textarea {
		resize: vertical;
		min-height: 120px;
	}
	
	.submit-button {
		width: 100%;
		padding: 1rem;
		font-size: 1.1rem;
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 0.5rem;
	}
	
	.submit-button:disabled {
		opacity: 0.7;
		cursor: not-allowed;
	}
	
	.spinner {
		width: 16px;
		height: 16px;
		border: 2px solid #fff;
		border-top: 2px solid transparent;
		border-radius: 50%;
		animation: spin 1s linear infinite;
	}
	
	@keyframes spin {
		0% { transform: rotate(0deg); }
		100% { transform: rotate(360deg); }
	}
	
	.success-message {
		background-color: #4caf50;
		color: #fff;
		padding: 1rem;
		border-radius: 5px;
		margin-bottom: 1.5rem;
		text-align: center;
		font-weight: 600;
	}
	
	@media (max-width: 768px) {
		.contact-container {
			grid-template-columns: 1fr;
			gap: 2rem;
		}
		
		.contact-info h2,
		.contact-form h2 {
			font-size: 1.5rem;
		}
		
		.contact-form {
			padding: 1.5rem;
		}
	}
</style>