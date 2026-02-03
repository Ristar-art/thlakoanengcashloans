<script>
	import apply from '$lib/assets/hero.jpg';
    import hero from "$lib/assets/pexels-kampus-8441817.jpg"
	import CV from '$lib/assets/cv.png';
    import Mobile from '$lib/assets/mobile.png'
    import Optiom from '$lib/assets/option.png'
	let formData = { name: '', email: '', phone: '', amount: '', period: '', repayment: '', terms: false };

	let idInput;
	let bankInput;
	let showTerms = false;

	function calculatePMT(principal, months) {
		if (!principal || !months || months <= 0) return 0;
		let p = parseFloat(principal);
		let n = parseInt(months);
		let total = p * 1.405; // flat interest added
		return total / n;
	}

	function calculateMonths(principal, pmt) {
		if (!principal || !pmt || pmt <= 0) return 0;
		let p = parseFloat(principal);
		let targetPMT = parseFloat(pmt);
		let total = p * 1.405;
		return Math.ceil(total / targetPMT);
	}

	$: calculatedPayment = calculatePMT(formData.amount || 0, formData.period || 1);

	$: if (formData.repayment && formData.amount) {
		formData.period = calculateMonths(formData.amount || 0, formData.repayment || 0).toString();
	}

	function handleSubmit() {
		// Handle form submission, e.g., send to API
		alert('Application submitted!');
	}
</script>
<section style="width: 100%; height:60vh; background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url({hero}); background-size:cover; background-position:center; display: flex; justify-content:center; align-items:center;">
    <h1 style="color: #ffd900;">Apply For Finance
    </h1>
   </section>
   
   <section class="apply-container">
    <div class="form-section">
        <h2>Apply Now!</h2>
        <form on:submit|preventDefault={handleSubmit}>
            <div class="top-inputs">
                <input type="text" placeholder="Full Name" bind:value={formData.name} required />
                <input type="email" placeholder="Email" bind:value={formData.email} required />
            </div>
            <input type="tel" placeholder="Phone Number" bind:value={formData.phone} required />
            <select bind:value={formData.amount} required>
                <option value="" disabled selected>Select Loan Amount</option>
                <option value="100">R 100.00</option>
                <option value="200">R 200.00</option>
                <option value="300">R 300.00</option>
                <option value="400">R 400.00</option>
                <option value="500">R 500.00</option>
                <option value="600">R 600.00</option>
                <option value="700">R 700.00</option>
                <option value="800">R 800.00</option>
                <option value="900">R 900.00</option>
                <option value="1000">R 1000.00</option>
                <option value="1500">R 1500.00</option>
                <option value="2000">R 2000.00</option>
                <!-- <option value="2500">R 2500.00</option>
                <option value="3000">R 3000.00</option>
                <option value="3500">R 3500.00</option>
                <option value="4000">R 4000.00</option>
                <option value="4500">R 4500.00</option>
                <option value="5000">R 5000.00</option>
                <option value="6000">R 6000.00</option>
                <option value="7000">R 7000.00</option>
                <option value="8000">R 8000.00</option>
                <option value="9000">R 9000.00</option>
                <option value="10000">R  10000.00</option>
                <option value="11000">R 11000.00</option>
                <option value="10000">R 10000.00</option>
                <option value="15000">R 15000.00</option>
                <option value="20000">R 20000.00</option>
                <option value="25000">R 25000.00</option>
                <option value="30000">R  30000.00</option>
                <option value="40000">R 40000.00</option>
                <option value="50000">R 50000.00</option>
                <option value="60000">R 60000.00</option>
                <option value="70000">R 70000.00</option>
                <option value="80000">R 80000.00</option>
                <option value="90000">R 90000.00</option>
                <option value="100000">R 100000.00</option>
                <option value="150000">R 150000.00</option>
                <option value="200000">R 200000.00</option>
                <option value="300000">R 300000.00</option>
                <option value="350000">R 350000.00</option> -->
            </select>
            <!-- <select bind:value={formData.period} required>
                <option value="" disabled selected>Select Repayment Period</option>
                <option value="1">1 Month</option>
                <option value="3">3 Months</option>
                <option value="6">6 Months</option>
                <option value="9">9 Months</option>
                <option value="12">12 Months</option>
                <option value="18">18 Months</option>
                <option value="24">24 Months</option>
                <option value="30">30 Months</option>
                <option value="36">36 Months</option>
                <option value="42">42 Months</option>
                <option value="48">48 Months</option>
                <option value="54">54 Months</option>
                <option value="60">60 Months</option>
                <option value="66">66 Months</option>
                <option value="72">72 Months</option>
            </select> -->
            {#if calculatedPayment > 0}
                <p style="color: #a30000;">Calculated Payment For The One Month: R {calculatedPayment.toFixed(2)}</p>
            {/if}
            <!-- <input type="number" placeholder="Desired Monthly Repayment" bind:value={formData.repayment} /> -->
            <div>
                <p style="color: #a30000;">Please upload a valid ID and your latest 3 months bank statements.</p>
                <button class="apply-button" type="button" on:click={() => idInput?.click()}>Upload ID</button>
                <input bind:this={idInput} type="file" accept="image/*,application/pdf" style="display: none" />
                <button class="apply-button" type="button" on:click={() => bankInput?.click()}>Upload Statement</button>
                <input bind:this={bankInput} type="file" accept="image/*,application/pdf" style="display: none" />
            </div>
            <label>
                <input type="checkbox" bind:checked={formData.terms} required />
                I accept the <button type="button" class="terms-link" on:click={() => showTerms = true}>terms and privacy policy</button>.
            </label>
            <button class="apply-button" type="submit">Submit Application</button>
        </form>
    </div>
    <div class="image-section">
        <img src={apply} alt="Apply for finance" />
    </div>
</section>


<style>
    .apply-container {
        width: 1200px;
        max-width: 1200px;
        margin: 100px auto;
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 4rem;
    }
    
    .form-section {
        width: 45%;
        background: rgba(255, 255, 255, 0.95);
        padding: 2.5rem;
        border-radius: 8px;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }
    
    .image-section {
        height: 75%;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    
    .image-section img {
        width: 100%;
        height: auto;
        border-radius: 8px;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }
    .text-section {
        flex: 2;
        color: #a30300;
        text-align: left;
        display: flex;
        flex-direction: column;
        /* justify-content: flex-end; */
    }
    h1 {
        color: white;
        /* color: #a30300; */
        margin-bottom: 20px;
    }
    p {
        color: white;

        /* color: #a30300; */
        margin: 10px 0;
    }
    form {
        display: flex;
        flex-direction: column;
        gap: 15px;
    }
    input, select {
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 4px;
    }
    
  
    @media (max-width: 768px) {
        .apply-container {
            flex-direction: column;
            gap: 2rem;
            padding: 0 20px;
        }
        
        .form-section,
        .image-section {
            width: 100%;
        }
        
        .form-section {
            padding: 1.5rem;
        }
        
        .steps {
            flex-direction: column;
            align-items: center;
        }
        .step-block {
            height: auto;
        }
        .top-inputs {
            flex-direction: column;
        }
        .info-section {
            padding: 10px;
        }
    }

    .modal-backdrop {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.5);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 1000;
    }

    .modal-content {
        background: white;
        border-radius: 8px;
        max-width: 800px;
        max-height: 80vh;
        overflow-y: auto;
        padding: 20px;
        position: relative;
    }

    .modal-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }

    .modal-header h2 {
        margin: 0;
        color: #a30300;
    }

    .close-btn {
        background: none;
        border: none;
        font-size: 24px;
        cursor: pointer;
        color: #a30300;
    }

    .modal-body {
        line-height: 1.6;
    }

    .modal-body h3 {
        color: #a30300;
        margin-top: 20px;
        margin-bottom: 10px;
    }

    .modal-body p, .modal-body ul, .modal-body ol {
        margin-bottom: 15px;
    }

    .modal-body ul, .modal-body ol {
        padding-left: 20px;
    }

    .terms-link {
        background: none;
        border: none;
        color: #ffd900;
        cursor: pointer;
        text-decoration: underline;
        padding: 0;
        font-size: inherit;
    }
    .top-inputs {
        display: flex;
        gap: 10px;
        justify-content: space-between;
    }
    .steps {
        display: flex;
        flex: 1 1 auto;
        justify-content: center;
        align-items: center;
    }
    .step-block {
        flex: 1;
        text-align: center;
        padding: 20px;
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 320px;
        justify-content: center;
    }
    .who-can-apply {
    margin-top: 50px;
    background-size: cover;
    background-position: center;
    padding: 20px;
    position: relative;
    border-radius: 8px;
    overflow: hidden;
    max-width: 1200px;  
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 4rem;
    display: flex;
}

/* Background overlay */
.who-can-apply::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 1;
}

.who-can-apply-overlay,
.who-can-apply-content {
    position: relative;
    z-index: 10;
    flex: 1;
    padding: 20px;
}

.who-can-apply-overlay {
    /* background-color: rgba(163, 3, 0, 0.1); */
    border-radius: 8px;
    padding: 30px;
}

.who-can-apply-overlay li {
    color: white;
    margin-bottom: 15px;
    list-style-position: inside;
}

.who-can-apply-content {
    /* background-color: rgba(255, 217, 0, 0.1); */
    border-radius: 8px;
    padding: 30px;
}

.who-can-apply-content ol {
    color: white;
    padding-left: 20px;
}

.who-can-apply-content ol li {
    margin-bottom: 10px;
}

.who-can-apply-title {
    font-size: 2.5rem;
    line-height: 1.2;
    font-weight: 700;
    margin-bottom: 2rem;
    color: #ffd900;
    text-align: start;
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