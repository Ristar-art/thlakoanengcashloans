<script>
	import hero from '$lib/assets/question.jpg';
     import Question from '$lib/assets/question-mark.jpg';
	
	let activeItem = null;
	
	function toggleAccordion(index) {
		activeItem = activeItem === index ? null : index;
	}
	
	const faqItems = [
		{
			question: "What is Thlakoaneng Cash Loans?",
			answer: "Thlakoaneng Cash Loans helps South Africans in the search for loans from different banks and lenders through our loan broker partners.\n\nWe provide access to up to 19 reputable banks and lenders. By completing our loan application you will get multiple loan offers, which you can compare and select the most suitable offer.\n\nThe service we offer is completely free of charge and you will not commit to anything by requesting for loan offers via Arcadia Finance. We only work with trusted loan brokers who collaborate with NCR licensed banks and lenders in South Africa."
		},
        {
           question: "What are the basic requirements for borrowing money",
           answer: "You are over 18 years old <br/> You are employed and employment has lasted for more than 6 months <br/> Your loan should not be more than 8 times larger than your monthly income"
        },
		{
			question: "Will I be acceptable for a loan?",
			answer: "This totally depends on the lenders. Each loan provider will have different terms and amounts that they offer based on your circumstances. If you have a good credit history and earn enough to cover the repayment amounts, there shouldn't be any problem getting a loan."
		}
	];
</script>

<section style="width: 100%; height:60vh; background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url({hero}); background-size:cover; background-position:center; display: flex; justify-content:center; align-items:center;">
	<h1 style="color: #ffd900;">Frequently Asked Questions</h1>
</section>

<section style="width: 1200px; max-width: 1200px; margin: 100px auto; padding: 0 20px;">
	<div class="faq-container">
		{#each faqItems as item, index}
			<div class="faq-item">
				<button 
					class="faq-question" 
					on:click={() => toggleAccordion(index)}
					aria-expanded={activeItem === index}
					aria-controls={`faq-answer-${index}`}
				>
					<span>{item.question}</span>
					<span class="faq-icon" class:active={activeItem === index}>
						<i class="fas fa-chevron-down"></i>
					</span>
				</button>
				<div 
					class="faq-answer" 
					class:active={activeItem === index}
					id={`faq-answer-${index}`}
				>
					<div class="answer-content">
						{@html item.answer.replace(/\n\n/g, '</p><p>').replace(/\n/g, '<br>')}
					</div>
				</div>
			</div>
		{/each}
	</div>
</section>

<section class="cta" style="background-image: url({Question})"> 
    <div class="cta-content">
        <h1 class="cta-title">
            Still have questions? Contact us today!
        </h1>
        <button class="apply-button">
            <a href="/contact">Contact</a>
        </button>
    </div>
</section>

<style>
	.faq-container {
		max-width: 800px;
		margin: 0 auto;
	}
	
	.faq-item {
		margin-bottom: 1rem;
		border-radius: 8px;
		overflow: hidden;
		background-color: #fff;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
		transition: box-shadow 0.3s ease;
	}
	
	.faq-item:hover {
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
	}
	
	.faq-question {
		width: 100%;
		padding: 1.5rem;
		background-color: #fff;
		border: none;
		text-align: left;
		font-size: 1.1rem;
		font-weight: 600;
		font-family: 'Rubik', sans-serif;
		color: #333;
		cursor: pointer;
		display: flex;
		justify-content: space-between;
		align-items: center;
		transition: background-color 0.3s ease;
	}
	
	.faq-question:hover {
		background-color: #f8f8f8;
	}
	
	.faq-icon {
		transition: transform 0.3s ease;
		color: #a30300;
		font-size: 0.9rem;
	}
	
	.faq-icon.active {
		transform: rotate(180deg);
	}
	
	.faq-answer {
		max-height: 0;
		overflow: hidden;
		transition: max-height 0.3s ease, padding 0.3s ease;
		background-color: #fff;
	}
	
	.faq-answer.active {
		max-height: 500px;
		padding: 0 1.5rem 1.5rem 1.5rem;
	}
	
	.answer-content {
		color: #666;
		line-height: 1.6;
		font-family: 'Roboto', sans-serif;
	}
	
	.answer-content p {
		margin-bottom: 1rem;
	}
	
	.answer-content p:last-child {
		margin-bottom: 0;
	}
	
	.cta {
		margin-top: 50px;
		background-size: cover;
		background-position: center;
		position: relative;
		border-radius: 8px;
		overflow: hidden;
		width: 1200px;
		max-width: 1200px;  
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 4rem;
		padding: 60px 20px;
	}

	.cta::before {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		background-color: rgba(0, 0, 0, 0.5);
		z-index: 1;
	}

	.cta-content {
		position: relative;
		z-index: 2;
		text-align: center;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.cta-title {
		font-size: 2.5rem;
		line-height: 1.2;
		font-weight: 700;
		margin-bottom: 2rem;
		color: #ffd900;
		text-align: center;
		max-width: 800px;
	}
	
	@media (max-width: 768px) {
		.faq-question {
			padding: 1rem;
			font-size: 1rem;
		}
		
		.faq-answer.active {
			padding: 0 1rem 1rem 1rem;
		}
		
		.cta-title {
			font-size: 1.8rem;
		}
	}
</style>