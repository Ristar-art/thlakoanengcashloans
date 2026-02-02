<script>
	import hero from '$lib/assets/hero.jpg';
</script>

<section style="width: 100%; height:40vh; background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url({hero}); background-size:cover; background-position:center; display: flex; justify-content:center; align-items:center;">
 <h1 style="color: #ffd900;">About Us</h1>
</section>

<section style="width: 1200px;  margin: 100px auto; display:flex">
<img src={hero} alt="" style="width: 50%;">
<div style=" padding: 60px 20px">
<h2>About Thlakoaneng Cash Loans
</h2>
<p>
    Thlakoaneng Cash Loans helps South Africans in the search for loans from different banks and lenders through our loan broker partners.
</p>
<p>
    We provide access to up to 19 reputable banks and lenders. By completing our loan application you will get multiple loan offers, which you can compare and select the most suitable offer.
</p>
<p>
    The service we offer is completely free of charge and you will not commit to anything by requesting for loan offers via Arcadia Finance. We only work with trusted loan brokers who collaborate with NCR licensed banks and lenders in South Africa.
</p>
<button class="apply-button">
    <a href="/contact">Contact</a>
</button>
</div>
</section>
<section class="cta" style="background-image: url({hero})"> 
    <div class="cta-content">
        <h1 class="cta-title">
            You will receive a response after completing the<br/> loan application with our current offers!!!
        </h1>
        <button class="apply-button">
            <a href="/apply">Apply</a>
        </button>
    </div>
</section>
<style>
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

/* Background overlay */
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

@media (min-width: 768px) {
    .who-can-apply-title {
        font-size: 2rem;
    }
}

@media (max-width: 768px) {
    .who-can-apply {
        flex-direction: column;
    }
    
    .who-can-apply-overlay,
    .who-can-apply-content {
        padding: 20px;
    }
    
    .who-can-apply-title {
        font-size: 2rem;
    }
}
</style>