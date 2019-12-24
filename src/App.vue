<template>
  <div id="app">
    <navigation></navigation>
    <div class="content">
      <balance></balance>
      <div class="services">
        <h2 class="page_title">Сервисы</h2>
        <filterSearch @change='onchange' @reset="onreset"></filterSearch>
        
        <div class="cards">
          <cardsComponent v-for="(card, idx) in cards['bonuses']" v-bind:key="idx" v-bind:data="card"></cardsComponent>
          <p class="error" v-if='error'>{{error}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navigation from './components/navigation.vue'
import balance from './components/balance.vue'
import filterSearch from './components/filter.vue'
import cardsComponent from './components/card.vue'
import cardsJson from "./assets/data.json";
export default {
  name: 'app',
  components: {
    Navigation, balance, filterSearch, cardsComponent
  },
  data () {
    return {
      resCards: cardsJson.bonuses.slice(),
      cards: cardsJson,
      error: ''
    }
  },
  methods: {
    onchange (data) {
      this.cards.bonuses = this.resCards
      this.cards.bonuses = this.cards.bonuses.filter(card => {
        return card.title.toLowerCase().includes(data.text.toLowerCase()) 
      })
      if(this.cards.bonuses.length == 0){
        this.error = 'Not found!'
      }
    },
    onreset (data){
      this.cards.bonuses = this.resCards  
    }
  },
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Roboto|Rubik&display=swap');
@import url('https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.min.css');
  body{
    background: #E5E5E5;
  }
  .content{
    margin-left: 80px;
    font-family: 'Roboto';
  }
  .services{
    padding: 40px 32px;
    background: #E5E5E5;
  }
  .page_title{
    font-family: 'Rubik';
    font-size: 39px;
    line-height: 46px;
    color: #262626;
    padding-bottom: 16px;
  }
</style>
