<template>
  <div id="app">
    <Header></Header>
    <div class="content">
      <Tabs :tabsContent="tabData"></Tabs>
    </div>
  </div>
</template>

<script>
import '@/assets/sass/main.sass'
import Header from './components/Header.vue'
import Tabs from './components/Tabs.vue'

export default {
  name: 'app',
  components: {
    Tabs,
    Header
  },
  data: function(){
    return {
      tabData: [
        {
          id: 1,
          title: "Overview",
          category: "overview"
        },
        {
          id: 2,
          title: "Getting started",
          category: "getting-started"
        },
        {
          id: 3,
          title: "Direct debit",
          category: "direct-debit"
        },
        {
          id: 4,
          title: "Developer Api",
          category: "developer-api"
        },
        {
          id: 5,
          title: "Paylinks",
          category: "paylinks"
        },
        {
          id: 6,
          title: "Partners",
          category: "partners"
        },
        {
          id: 7,
          title: "The customer experience",
          category: "customer-experience"
        },
        {
          id: 8,
          title: "Security",
          category: "security"
        },
        {
          id: 9,
          title: "Refunds and Chargebacks",
          category: "refunds-chargebacks"
        },
        {
          id: 10,
          title: "International Payments",
          category: "international-payments"
        },
      ]
    }
  }
}
</script>