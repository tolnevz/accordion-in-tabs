<template>
    <div class="tab-wrapper">
      <div class="tab-nav">
        <ul @click="activate" :class="{ 'is-open' : isActive }">
          <li @click="selectTab(item.id, item.category)" 
              v-for="item in tabsContent" 
              :key="item.id" 
              :class="{ 'active' : currentTab == item.id }">{{ item.title }}</li>
        </ul>
      </div>
      
      <div class="tab-content">
        <div v-for="item in tabsContent" :key="item.id">
          <div v-if="currentTab == item.id">
            
              <Accordion :accordionContent="newData"></Accordion>
          </div>
        </div>
      </div>

    </div>
</template>

<script>

import Accordion from './Accordion.vue'

export default {
  name: 'Tabs',
  components: {
    Accordion,
  },
  props: {
    tabsContent: Array
  },
  data: function(){
    return {
      currentTab: 1,
      isActive: false,
      currentCategory: "overview",
      accordionData: [
        {
          id: 1,
          category: "overview",
          title: "How can I use GoCardless?",
          description: "<p>There are three ways to use GoCardless:</p> <ul><li><strong>Our dashboards</strong>&nbsp;- Set up and manage Direct Debit payments with your customers using our simple online dashboard.</li><li><strong>Our account software partnerships</strong>&nbsp;- We work with a growing list of&nbsp;<a href='#'>partners</a>, so you can take payments within the online services you already use.</li><li><strong>Our clean, RESTful API</strong>&nbsp;- Integrate GoCardless into your website using our&nbsp;<a href='#'>REST API</a>.</li></ul>",
          active: false
        },
        {
          id: 2,
          category: "overview",
          title: "Who is GoCardless for?",
          description: "<p>GoCardless the first global network for <a href='#'>recurring payments</a>, and is for anyone who wants to take payments directly from the bank account of customers in more than 30 countries, including in the UK, USA, the Eurozone, Sweden, Denmark, Australia, New Zealand and Canada. You can also collect payments in your customers’ currency, settle in your own, at the real exchange rate.</p><p>Our easy-to-use dashboards and powerful API make GoCardless a powerful platform for everyone from innovative start-ups to multi-national corporations.</p><p>GoCardless has integrated with over 200 of the most popular billing platforms, CRMs, accounting packages, and more to enable easy recurring payment collection. Find out more <a href='#'>here</a>.</p>",
          active: false
        },
        {
          id: 3,
          category: "overview",
          title: "What can I not use GoCardless for?",
          description: "<p>GoCardless is great for many use cases. However, there are some limitations with our service. We aren’t able to:</p><ul><li><strong>Let you take credit card payments</strong>&nbsp;- however you&nbsp;<strong>can</strong>&nbsp;use another payment provider alongside GoCardless.</li><li><strong>Let you accept instant payments</strong>&nbsp;- Direct Debit payments take 3-5 working days to clear, so they’re not ideal for goods that need to be shipped quickly.</li></ul>  <p>We’re able to accept most kinds of customers but there are some exceptions - for full details, see our&nbsp;<a href='#'>restricted activities page</a>.</p>",
          active: false
        },
        {
          id: 4,
          category: "overview",
          title: "Are there any limits on the amount I can collect?",
          description: "<p>There are no limits on how many transactions you can make.</p><p>There is, however, a limit on the maximum amount that can be collected in a single transaction. These are:</p> <ul> <li>UK £5000 GBP (with a minimum transaction amount of £1)</li>    <li>Australia $10,000 AUD</li><li>New Zealand $10,000 NZD</li><li>Canada $5,000 CAD</li><li>Eurozone €5000 EUR</li><li>Sweden 20M SEK</li><li>Denmark kr.50,000 DKK</li></ul><p>We may be able to increase these limits with additional verification checks.</p>",
          active: false
        },
        {
          id: 5,
          category: "overview",
          title: "How do I receive funds I have collected with GoCardless?",
          description: "<p>The funds collected are paid directly into your bank account.</p> <p>With GoCardless, our&nbsp;<a href='#'>fees</a>&nbsp;are deducted automatically.</p><p>With GoCardless Pro, we’ll send you an invoice for your&nbsp;<a href='#'>fees</a>.</p>",
          active: false
        },
        {
          id: 6,
          category: "overview",
          title: "When do I receive my payment?",
          description: "<p>All payments are paid out 2 working days from when the payment was collected.</p>  <p>We don’t hold back any of your funds in reserve.</p>",
          active: false
        },
        {
          id: 7,
          category: "overview",
          title: "Do you take credit or debit cards?",
          description: "<p>No, GoCardless is a Direct Debit company.</p>",
          active: false
        },
        {
          id: 8,
          category: "overview",
          title: "Is GoCardless a Bacs-approved bureau?",
          description: "<p>Yes, GoCardless is a Bacs-approved bureau.</p>",
          active: false
        },
        {
          id: 9,
          category: "getting-started",
          title: "When do I receive my payment?",
          description: "<p>We automatically pay out funds to your specified bank account&nbsp;<strong>3 working days</strong>&nbsp;after they’re collected from your customer. You can see more details&nbsp;<a href='#'>here</a>.</p>",
          active: false
        },
        {
          id: 10,
          category: "getting-started",
          title: "What types of payments can I collect?",
          description: "<p>You can collect one-off, regular or variable Direct Debit payments with our simple online tool or the API.</p>",
          active: false
        },
        {
          id: 11,
          category: "getting-started",
          title: "How does the payment process work?",
          description: "  <ul><li>Using our online tool you can issue a request for authorisation to take Direct Debit payments from a customer in 2 clicks.</li><li>We email your customer a link to our payment authorisation page. To authorise they click the link and complete our secure checkout.</li><li>Once authorised, you can take payments from your customers automatically by adding them to a payment plan.</li><li>We will notify your customers every time a new payment is taken.</li></ul>",
          active: false
        },
        {
          id: 12,
          category: "getting-started",
          title: "How does my customer authorise a payment?",
          description: "<p>You can trigger a request for authorisation from GoCardless by adding a customer, or send them a link to a plan yourself.</p><p>Your customer just needs to click the link and enter their details on our secure online payment page to set up a Direct Debit and authorise you to take future payments automatically.</p>",
          active: false
        },
        {
          id: 13,
          category: "getting-started",
          title: "Can customers sign up on my website?",
          description: "<p>Yes - you can either do this by integrating with our&nbsp;<a href='#'>API</a>&nbsp;or by generating a link for a payment plan and embedding this as a button on your website.</p><p>On clicking the button the customer will be sent to our secure online payment page where they can authorise the payment(s).</p>",
          active: false
        },
        {
          id: 14,
          category: "getting-started",
          title: "Can I set payments to start and end on a particular date?",
          description: "<p>Yes - you can easily customise the day, date, frequency and duration of payments.</p>",
          active: false
        },
        {
          id: 15,
          category: "getting-started",
          title: "Can I change a payment or payment plan once it has been created?",
          description: "<p>Provided your payment hasn’t been submitted to the banks yet, you can easily cancel an existing payment or remove your customer from the plan and add them to a new one. All this can be done from within your dashboard in seconds.</p>",
          active: false
        },
        {
          id: 16,
          category: "getting-started",
          title: "How do I know if I’ve been paid?",
          description: "<p>Our online dashboard gives you real-time info on all your payments and customers, allowing you to check the status of a payment at any time.</p>",
          active: false
        },
        {
          id: 17,
          category: "getting-started",
          title: "Will you ever place limits on my account?",
          description: "<p>There are certain situations where it may be necessary to place restrictions on your account:</p><ul><li>Where we believe that there may be a breach in the security of your account details;</li><li>Where we suspect the unauthorised or fraudulent use of your account;</li><li>Where we are required to by law.</li></ul><p>If we ever do have to do this, rest assured we will notify you as soon as possible and make sure that there is always someone you can talk to to help resolve the situation as quickly as possible.</p>",
          active: false
        },
        {
          id: 18,
          category: "direct-debit",
          title: "What is Direct Debit?",
          description: "<p>There are certain situations where it may be necessary to place restrictions on your account:</p><p>If we ever do have to do this, rest assured we will notify you as soon as possible and make sure that there is always someone you can talk to to help resolve the situation as quickly as possible.</p>",
          active: false
        },
        {
          id: 19,
          category: "direct-debit",
          title: "What is the Direct Debit Guarantee?",
          description: "<p><a href='#'>The Direct Debit Guarantee</a>&nbsp;offers protection to customers paying by Direct Debit in the rare event that there is an error in a payment.</p><p>If a customer receives a refund they are not entitled to, they must pay it back at the organisation’s request. Dispute resolution takes place outside of the Direct Debit scheme.</p>",
          active: false
        },
        {
          id: 20,
          category: "direct-debit",
          title: "What kind of payments is it good for?",
          description: "<p>They are particularly good for:</p><ul><li>Regular payments (e.g., subscriptions or regular donations)</li><li>Customers with an ongoing relationship (e.g., account customers)</li><li><a href='#'>Invoicing</a> for services (e.g., accountancy, tax advice, etc.)</li></ul>",
          active: false
        },
        {
          id: 21,
          category: "direct-debit",
          title: "What kind of payments isn’t it good for?",
          description: "<ul><li>Transactions which need an instant clearing (e.g., e-commerce)</li><li>High-value, one-off payments for liquid goods (e.g., gold bullion)</li><li>Transactions likely to experience chargebacks (e.g., gambling)</li></ul>",
          active: false
        },
        {
          id: 22,
          category: "direct-debit",
          title: "What are the payment timings for Direct Debit?",
          description: "<p>Unlike card payments, Direct Debits don’t clear instantly. Instead, it takes 3 days to set up each new payer, and to collect from payers who you currently have a Direct Debit relationship with.</p><p>Once GoCardless has collected payment from your customer we hold the money for 3 working days before sending it directly to your bank account.</p>",
          active: false
        },
        {
          id: 23,
          category: "direct-debit",
          title: "Can I collect one-off payments using Direct Debit?",
          description: "<p>Yes - although Direct Debit is most well-known for <a href='#'>recurring payments</a>, it can also be used to collect one-off payments.</p>",
          active: false
        },
        {
          id: 24,
          category: "developer-api",
          title: "What can I use the API for?",
          description: "<p>Our REST API allows developers to easily create powerful integrations with GoCardless. See our documentation to find out more.</p><p>You can integrate as a Merchant to take payments on your own behalf, or integrate as a Partner to create and manage multiple merchants.</p>",
          active: false
        },
        {
          id: 25,
          category: "developer-api",
          title: "How does the Partner API work?",
          description: "<p>A Partner integration allows your customers to quickly and easily create a GoCardless account without copying and pasting API keys.</p><p>This account will be linked to your Master Merchant account so that you can manage these accounts and process payment requests on their behalf.</p><p>For further information, see our <a href='#'>partner API guide.</a></p>",
          active: false
        },
        {
          id: 26,
          category: "developer-api",
          title: "What programming languages can I use?",
          description: "<p>We have client libraries for Ruby, PHP, Java, Python and .NET</p>",
          active: false
        },
        {
          id: 27,
          category: "developer-api",
          title: "Can I host the payment pages on my site?",
          description: "<p>Yes, but only with GoCardless Pro. With Pro, you’re able to design your own payment pages and you can host them directly on your website.</p><p>On our Standard or Plus packages, we host the payment pages securely on our website in order to comply with the Direct Debit scheme rules.</p><p>You can redirect the customer to our payment page and we will redirect them back to your site. Alternatively, you can allow customers to access the payment pages via a pop-up from your website.</p>",
          active: false
        },
        {
          id: 28,
          category: "paylinks",
          title: "Where does my business need to be based?",
          description: "<p>Businesses can sign up to collect payments through GoCardless if they are based in any of the following countries:</p> <ul><li>Australia</li><li>Austria</li><li>Belgium</li><li>Bulgaria</li><li>Canada</li><li>Croatia</li><li>Cyprus</li><li>Czech Republic</li><li>Denmark</li><li>Finland</li><li>France</li><li>Germany</li><li>Hungary</li><li>Italy</li><li>Luxembourg</li><li>Malta</li><li>Netherlands</li><li>New Zealand</li><li>Norway</li><li>Poland</li><li>Portugal</li><li>Republic of Ireland</li><li>Romania</li><li>Slovakia</li><li>Slovenia</li><li>South Africa</li><li>Spain</li><li>Sweden</li><li>Switzerland</li><li>United Kingdom</li><li>United States</li></ul>",
          active: true
        },
        {
          id: 29,
          category: "partners",
          title: "What happened to the old referral scheme?",
          description: "<p>Our previous referral scheme was closed on February 29th, 2016. All sign-ups made on or after this date no longer qualify for the referral incentive.</p>",
          active: false
        },
        {
          id: 30,
          category: "partners",
          title: "I’ve referred a friend to GoCardless. What happens to my GoCardless credit?",
          description: "<p>Our old referral scheme is now closed and payouts from that referral scheme will stop from the 30th June 2016. Instead we will be offering all those businesses who have outstanding credits from the referral scheme a rebate of transaction fees for all transactions processed by GoCardless from 1st July 2016 until the 30th November 2016, subject to fair use (and other detail as set out in the T&Cs). All eligible businesses will receive an email to confirm that they will receive a one-off credit of the cumulative transaction fee amount by the 16th December 2016 - please note this will be processed automatically and paid out to the bank account we hold on file for you on the payment date.</p>",
          active: false
        },
        {
          id: 31,
          category: "partners",
          title: "What happens to my old referral links?",
          description: "<p>Our previous referral scheme was closed on February 29th, 2016. Anyone signing up through a referral link from this programme after this date will see a message on the sign-up page stating the scheme is no longer available.</p>",
          active: false
        },
        {
          id: 32,
          category: "customer-experience",
          title: "Can I fill in the payment pages on my customer’s behalf?",
          description: "<p>No - due to strict rules around Direct Debit, customers must fill in their payment details and go through the signup process themselves.</p>",
          active: false
        },
        {
          id: 33,
          category: "customer-experience",
          title: "Will my name appear on my customer’s bank statement?",
          description: "<p>With GoCardless, your business name will normally appear on the bank statement as the reference for the Direct Debit with GoCardless as the recipient. With GoCardless Plus or Pro, only your business name will appear on the bank statement for domestic payment collections.</p><p>When you collect international payments from customers, customers will always see 'GoCardless Ltd' on their bank statements.</p><p>You can customise how we display your business name on customer bank statements from the Settings page of your merchant dashboard.</p>",
          active: false
        },
        {
          id: 34,
          category: "customer-experience",
          title: "How can my customer pay me?",
          description: "<p>Your customer can enter their bank details online via GoCardless; if you use GoCardless Pro they can also do so by phone or paper.</p>",
          active: false
        },
        {
          id: 35,
          category: "customer-experience",
          title: "Do you offer iFrames?",
          description: "<p>No - we do not offer iFraming of our payment pages. If you use GoCardless Pro, we offer a Flow JS which lets you avoid having any bank data on your server.</p>",
          active: false
        },
        {
          id: 35,
          category: "security",
          title: "How do I know my money is safe?",
          description: "<p>We are authorised by the Financial Conduct Authority to provide payment services as an <a href='#'>Authorised Payment Institution</a>. We serve more businesses than any other Direct Debit provider.</p><p>All money collected is held in a secure client monies account with either the Royal Bank of Scotland, Barclays Bank, SEB, NAB or ASB.</p>",
          active: false
        },
        {
          id: 36,
          category: "security",
          title: "What is ISO 27001 certification?",
          description: "<p>GoCardless has been awarded ISO 27001 certification. ISO 27001 is a widely recognised, internationally accepted standard for information security and we have attained it across all GoCardless services and products.</p><p>An accredited independent auditor has assessed our processes and controls, and confirmed they align with the certification standard. Certification Europe, an ISO accredited certification body, has certified our compliance with the ISO standard.</p><p>Having ISO 27001 certification helps assure our merchants and their customers that we take information security management seriously. GoCardless will ensure that an independent auditor will reassess our Information Security Management System on an annual basis.</p>",
          active: false
        },
        {
          id: 37,
          category: "security",
          title: "Is it safe for my customers?",
          description: "<p>Yes. Your customers are fully protected by the Direct Debit Guarantee. This entitles them to a full and immediate refund of any payments taken from their account in error.</p>",
          active: false
        },
        {
          id: 38,
          category: "refunds-chargebacks",
          title: "Rules",
          description: "<p>When reporting vulnerabilities, please consider (1) attack scenario/exploitability, and (2) the security impact of the bug. The following issues are considered out of scope:</p><ul ><li>Denial of service attacks</li><li>Do not attempt to access or modify any user data that is not your own.</li><li>Do not degrade the performance of our services (e.g. via automated scanning, brute forcing, or denial of service attacks)</li><li>Social engineering attacks</li><li>Physical attacks or threats against our staff or users</li><li>Theoretical scenarios that do not demonstrate an impact.&nbsp; E.g. a tool reporting a weak cipher suite due to lack of Perfect Forward Secrecy.</li></ul>",
          active: false
        },
        {
          id: 39,
          category: "refunds-chargebacks",
          title: "What is Betalingsservice Direct Debit?",
          description: "<p>Betalingsservice allows you to collect Danish Krone-denominated payments from a bank account in Denmark. You can read more about it in our guide to Betalingsservice Direct Debit.</p>",
          active: false
        },
        {
          id: 40,
          category: "international-payments",
          title: "Where can my customers be based?",
          description: "<p>GoCardless gives you access to a growing number of Direct Debit (also known as bank debit) schemes around the world. When you collect <a href=''>international payments</a>, you can collect from your customers in their currencies, then have the payments converted into your home currency and paid out into your domestic bank account.</p><ul><li>United Kingdom - <a href='#'>Bacs Direct Debit</a></li><li>Eurozone - <a href='#'>SEPA Direct Debit</a> (for a full list of supported countries,&nbsp;<a href='#'>see this support article</a>)</li><li>Sweden - Bg Autogiro</li><li>Denmark - Betalingsservice</li><li>Australia - BECS Direct Debit</li><li>New Zealand - BECS Direct Debit</li><li>Canada - Pre-Authorized Debit</li><li>United States - ACH Debit</li></ul>",
          active: false
        },
        {
          id: 41,
          category: "international-payments",
          title: "What is Bacs Direct Debit?",
          description: "<p>Bacs Direct Debit allows you to collect GBP-denominated payments from a bank account in the United Kingdom. You can read more about it in our guide to Bacs Direct Debit.</p>",
          active: false
        },
        {
          id: 42,
          category: "international-payments",
          title: "What is SEPA Direct Debit?",
          description: "<p>SEPA Direct Debit allows you to collect Euro-denominated payments from a bank account in the Single Euro Payments Area (SEPA). You can read more about it in our guide to SEPA Direct Debit.</p>",
          active: false
        },
        {
          id: 43,
          category: "international-payments",
          title: "What is BECS Direct Debit?",
          description: "<p>BECS allows you to collect Australian Dollar-denominated payments from a bank account in Australia. You can read more about it in our guide to BECS Direct Debit.</p>",
          active: false
        },
        {
          id: 44,
          category: "international-payments",
          title: "What is BECS (NZ) Direct Debit?",
          description: "<p>BECS allows you to collect New Zealand Dollar-denominated payments from a bank account in New Zealand. You can read more about it in our guide to BECS Direct Debit.</p>",
          active: false
        },
        {
          id: 45,
          category: "international-payments",
          title: "What is ACH (US) Debit?",
          description: "<p>ACH Debit allows you to collect US Dollar-denominated payments from a bank account in the United States. You can read more about it in our guide to ACH Debit.</p>",
          active: false
        },
        {
          id: 46,
          category: "international-payments",
          title: "What is Pre-Authorized Debit (PAD)?",
          description: "<p>Pre-Authorized Debit (sometimes known as PAD) allows you collect Canadian dollar-denominated payments from a bank account in Canada. You can read more about it in our guide to Pre-Authorized Debit.</p>",
          active: false
        },
      ],
    }
  },
  methods: {
    selectTab(selectedTab, selectedCategory){
      this.currentTab = selectedTab;
      this.currentCategory = selectedCategory;
    },
    activate(){
      this.isActive = !this.isActive;
    }
  },
  computed: {
    newData(){
      var category = this.currentCategory;
      var oldArr = this.accordionData;
      var newArr = oldArr.filter(function(el){
        return el.category == category;
      });
      return newArr;
    }
  }
}
</script>
