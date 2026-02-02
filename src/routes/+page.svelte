	<script>
	import hero from '$lib/assets/vitaly-gariev.jpg';
	import CV from '$lib/assets/cv.png';
    import Mobile from '$lib/assets/mobile.png'
    import Optiom from '$lib/assets/option.png'
    import Money from '$lib/assets/money.jpg'
    import Coins from '$lib/assets/coins.jpg'

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

	$: calculatedPayment = calculatePMT(formData.amount || 0, formData.period || 0);

	$: if (formData.repayment && formData.amount) {
		formData.period = calculateMonths(formData.amount || 0, formData.repayment || 0).toString();
	}

	function handleSubmit() {
		// Handle form submission, e.g., send to API
		alert('Application submitted!');
	}
</script>

<section class="hero" style="background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url({hero}); background-size: cover; background-position: center;">
    <div class="hero-container">
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
                    <option value="2500">R 2500.00</option>
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
                    <option value="350000">R 350000.00</option>
                </select>
                <select bind:value={formData.period} required>
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
                </select>
                {#if calculatedPayment > 0}
                    <p style="color: #a30000;">Calculated Monthly Payment: R {calculatedPayment.toFixed(2)}</p>
                {/if}
                <input type="number" placeholder="Desired Monthly Repayment" bind:value={formData.repayment} />
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
                 <!-- <div class="g-recaptcha" data-sitekey="6LeIxAcTAAAAAJcZVRqyHh71UMIEGNQ_MXjiZKhI"></div> -->
                 <button class="apply-button" type="submit">Submit Application</button>
            </form>
        </div>
        <div class="text-section">
            <h1 style="font-size: 3rem; color: #ffd900">Personal Loans</h1>
            <p>Looking for a personal loan?</p>
            <p>Thlakoaneng Cash Loans will find your best options fast! Fill in a free application and get our current loan offers.</p>
        </div>
    </div>
</section>
<section style="width: 1200px; hight:800px; margin: 50px auto; padding:  20px; display:flex; ">

    <img src={Money} alt="" style="width: 50%; border-radius: 8px">
   <div style="width:50%; display:flex;flex-direction:column ;text-align:center; justify-content:center; align-items:center; padding-left:20px; padding-right:20px ">
       <h2>
        You will receive a response after completing the loan application with our current offers!!!

       </h2>
       <!-- <p style="color:black;">somethitf fdv;sk df;ousv .dkacxjv adkcjhgv ,ajsdcv amnsdchgv sa,dchva asjldgcv dksvj dsvba dsjhfv ifbvds udsfva jiusdfa jujsdfbai usdjab </p> -->
   </div>

</section>
<h1 id="easy-steps" style="color: black; text-align:center; margin-top: 20px">Get Assistance in 3 easy steps</h1>

<div  class="" style="padding: 20px; max-width: 1200px; margin: 0 auto; margin-top: 20px; border-radius: 8px; gap: 20px; display: flex; justify-content: space-around; flex-wrap: wrap; ">
        <div class="step-block" >
            <div class="icon-step">
             <img src={CV} alt="" style="width: 100px; height: 100px;"/>
            </div>
            
               
            <!-- </div> -->
            <h2> <strong>Fill in our application</strong></h2> 
            <p style="color: black;">
    
                Complete our loan application in minutes. Just enter your details and choose your desired loan amount.
             </p>
    
        </div>
        <div class="step-block" >
            <div class="icon-step">
                <img src={Optiom} alt="" style="width: 100px; height: 100px;"/>
                      </div>
            <h2><strong>Choose Best Option</strong> </h2>
            <p style="color: black;">
                Based on your responses, you will receive a variety of personalised offers from up to 19 lenders.

            </p>
        </div>
        <div class="step-block" >
            <div class="icon-step">
                <img src={Mobile} alt="" style="width: 100px; height: 100px;"/>
           </div>
           <div>
            
           </div>
            <h2><strong>Receive Your Money</strong></h2>
           
           <p style="color: black;">
            You are free to accept or decline the offers as you please. The offers are non-binding.

           </p> 
      
    </div>
     </div>   
    <section id = "who-can-apply" class="who-can-apply" style="background-image: url({Coins})"> 
         <div class="who-can-apply-overlay">
            <h1 class="who-can-apply-title">
                Why use Thlakoaneng Cash Loans?
            </h1>




             <li>100% free:The application is free and does not include any hidden fees.
            </li>

             <li>Quick & easy: The whole application process is done online in minutes.
            </li>

             <li>Convenient: Compare up to 19 banks & lenders from one application.
            </li>

             <li>Non-binding: You decide if you want to accept or decline your offers.
            </li>

             <li>Safe: Your personal data is safe with us.
            </li>


        </div>
            <div class="who-can-apply-content">
                <h1 class="who-can-apply-title">
                    Who can apply?
                </h1>
                <ol>
                    <li>You are over 18 years old</li>
                    <li>You are employed and employment has lasted for more than 6 months</li>
                    <li>Your loan should not be more than 8 times your monthly income</li>
                </ol>
               
            </div>
    </section>










{#if showTerms}
<div class="modal-backdrop" role="button" tabindex="0" on:click={() => showTerms = false} on:keydown={(e) => { if (e.key === 'Escape') showTerms = false; }}>
    <div class="modal-content" on:click|stopPropagation>
        <div class="modal-header">
            <h2>Terms of Service</h2>
            <button class="close-btn" on:click={() => showTerms = false}>×</button>
        </div>
        <div class="modal-body">
            <p style="color: black;">Thlakoaneng Cash Loans is a domestic service that helps you to apply a loan. We send your loan application in advance to a loan broker, who mediates it to banks and finance companies. Thlakoaneng Cash Loans markets, inter alia, licensed loan intermediary service provided by Leads Clinic. We also help you in loan application requests by comparing different banks and finance companies and share useful economic tips.</p>

            <p style="color: black;">By using ThlakoanengCashLoans.co.za service you provide an access for Thlakoaneng Cash Loans to your current information. Thlakoaneng Cash Loans possesses and operates the web service at www.ThlakoanengCashLoans.co.za. The purpose of this notification is to explain what types of data we collect, in what way and what we use it for.</p>

            <h3>What is personal data?</h3>
            <p style="color: black;">Personal data is information that can be associated with you, e.g., name, place of residence, phone number and email address. Personal data is also defined as information about how you use ThlakoanengCashLoans.co.za services, such as ads you have recently seen.</p>

            <h3>How is the processing of personal data regulated?</h3>
            <p style="color: black;">Thlakoaneng Cash Loans is responsible for processing all personal data collected through the ThlakoanengCashLoans.co.za service. The data is stored either in our database or on devices used (phone, laptop, etc.). You can be sure that all the personal data is being processed in accordance with the Data Protection Act.</p>

            <h3>What personal data do we collect?</h3>
            <p style="color: black;">1. Your own data We store a certain personal data you provide to us when singing up for ThlakoanengCashLoans.co.za service. The same happens when you fill out forms on our start-up page or elsewhere on the website.</p>
            <p style="color: black;">2. The information about how you visit ThlakoanengCashLoans.co.za website. We collect data about technologies you use, such as whether you use a laptop, tablet or smartphone, or which browser and network operator you use while visiting homepages on our website.</p>
            <p style="color: black;">3. The data about what actions do you take on our website. We receive an information about your behaviour on our website every time you visit it. We may also, inter alia, receive a data about what page you visited, what notifications you clicked on and what kind of advertisements we presented to you.</p>
            <p style="color: black;">4. The information required to apply for a loan</p>

            <p style="color: black;">The loan application data completed on page is stored in our database. Your personal ID (identification code) will only be stored in case of error for temporary period of one (1) week.</p>

            <h3>Who is responsible for processing of personal data?</h3>
            <p style="color: black;">The management of Thlakoaneng Cash Loans is responsible for processing of personal data related to company’s business. Liability concerns daily compliance of data protection principles implemented in business activity.</p>

            <h3>What does registration mean?</h3>
            <p style="color: black;">Signing up for ThlakoanengCashLoans.co.za service offers you various benefits. When applying for a loan, you will receive an important information via email, SMS or phone:</p>
            <ul>
                <li>about how to improve your chances of getting loan recommendations</li>
                <li>on how to improve your daily finance</li>
                <li>about banks offering the best refinancing and loan facilities</li>
                <li>financial news</li>
            </ul>
            <p style="color: black;">Expectedly, you will receive text messages from us a few times in a week. You can cancel receiving text messages by clicking on the cancellation link at the end of the message.</p>

            <h3>Why do we collect personal data?</h3>
            <p style="color: black;">We collect your personal data so we could offer you possibly suitable options and the best loan facilities among our companies. We keep you informed of all suitable offers using your contact information. The processing of personal data, storage and forwarding occurs in full accordance with the Data Protection Act.</p>

            <h3>What data is being used for?</h3>
            <p style="color: black;">Our purpose is to provide customised user experience for each ThlakoanengCashLoans.co.za user.</p>

            <p style="color: black;">We use personal data in order to…</p>
            <p style="color: black;">1. Provide you with the service you expect to receive from us. For example, we need your email address and mobile phone number so as to loan providers can contact you and offer a loan in accordance with your loan application request.</p>
            <p style="color: black;">2. Understand market needs and trends. We analyse data and use that information for our service further development. We can, for example, give you more detailed advice on how to improve your loan facilities or make you a better tailored loan offer.</p>
            <p style="color: black;">3. Prevent you from unwanted and criminal activities. One of our most important goals is to ensure that Thlakoaneng Cash Loans is safe place where to apply for a loan. For this reason, we do our best to prevent all unwanted and criminal activities. The information obtained through cookies as well as notification and message history is an important tool which helps to identify misconduct and fraud attempt. Service and data security working group monitors closely any possible suspicion of misconduct.</p>
            <p style="color: black;">4. Inform you about loan offers via email, SMS and phone.</p>

            <p style="color: black;">We will send you from time to time a loan offers information, that you might be interested in, by email, SMS and phone.</p>

            <h3>Who else gets the information?</h3>
            <p style="color: black;">The third parties may use your personal data with the goal of an analysis. All the third parties are obliged to follow our personal data processing policies. Your data may be forwarded to officials in a case of any suspicions of breaking a law. The information may be also forwarded in cases when fraud is still possible or when some disagreement can be resolved by using data.</p>

            <p style="color: black;">In individual cases, we provide your personal data to the companies with whom we cooperate with in CRM service or email/SMS marketing fields. Companies do not have the right to use your data for anything else besides service production to us.</p>

            <h3>Data collected by cookies</h3>
            <p style="color: black;">We use cookies in certain parts of our service. Those are small files containing data that are stored on your computer to improve user experience. This feature can be easily turned on/off in browser. If you decide to turn off the cookies, you will be able to use Thlakoaneng Cash Loans service in further, but some certain functions might not work optimally.</p>

            <h3>Remove of personal data</h3>
            <p style="color: black;">We do not store a personal data longer than it is purposefully necessary unless required by law. We have established personal and identifying data removing procedures, thus you can request data to be deleted. If you want to cancel a newsletter subscription, you can do this through the cancellation link at the end of newsletter you receive.</p>

            <p style="color: black;">Please contact us if you would like to remove own data from our system: info@ThlakoanengCashLoans.co.za</p>

            <p style="color: black;">You will receive a response after completing the loan application with our current offers!!!</p>

            <h3>Who can apply?</h3>
            <ul>
                <li>You are over 18 years old</li>
                <li>You are employed and employment has lasted for more than 6 months</li>
                <li>Your loan should not be more than 8 times your monthly income</li>
            </ul>

            <h3>Get Assistance in 3 easy steps</h3>
            <ol>
                <li><strong>Fill in our application</strong> Complete our loan application in minutes. Just enter your details and choose your desired loan amount.</li>
                <li><strong>Choose Best Option</strong> Based on your responses, you will receive a variety of personalised offers from up to 19 lenders.</li>
                <li><strong>Receive Your Money</strong> You are free to accept or decline the offers as you please. The offers are non-binding.</li>
            </ol>

            <h3>Why use Thlakoaneng Cash Loans?</h3>
            <ul>
                <li><strong>100% free:</strong> The application is free and does not include any hidden fees.</li>
                <li><strong>Quick & easy:</strong> The whole application process is done online in minutes.</li>
                <li><strong>Convenient:</strong> Compare up to 19 banks & lenders from one application.</li>
                <li><strong>Non-binding:</strong> You decide if you want to accept or decline your offers.</li>
                <li><strong>Safe:</strong> Your personal data is safe with us.</li>
            </ul>

            <h3>About Thlakoaneng Cash Loans</h3>
            <p style="color: black;">Thlakoaneng Cash Loans helps South Africans in the search for loans from different banks and lenders through our loan broker partners.</p>

            <p style="color: black;">We provide access to up to 19 reputable banks and lenders. By completing our loan application you will get multiple loan offers, which you can compare and select the most suitable offer.</p>

            <p style="color: black;">The service we offer is completely free of charge and you will not commit to anything by requesting for loan offers via Thlakoaneng Cash Loans. We only work with trusted loan brokers who collaborate with NCR licensed banks and lenders in South Africa.</p>

            <p style="color: black;">© 2025 Thlakoaneng Cash Loans.</p>
        </div>
    </div>
</div>
{/if}

<style>
    .hero {
        /* height: 100vh; */
        padding: 20px;
        min-height: 80vh;
        display: flex;
        align-items: center;
        justify-content: center;
        background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5))
    }
    .hero-container {
        display: flex;
        width: 100%;
        max-width: 1200px;
        gap: 40px;
    }
    .form-section {
        flex: 1;
        background: rgba(255, 255, 255, 0.9);
        padding: 20px;
        border-radius: 8px;
    }
    .text-section {
        flex: 2;
        color: #a30300;
        text-align: left;
        display: flex;
        flex-direction: column;
        justify-content: center;

    }
    h1 {
        color: white;
        /* color: #a30300; */
        margin-bottom: 20px;
        font-size: xx-large;
    }
    p {
        color  : white;
        font-size:x-large;
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
        .hero-container {
            flex-direction: column;
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