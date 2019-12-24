<template>
  <div class="balance">
      <div class="balance_item">
        <p class="balance_item_title">Баланс</p>
        <p class="balance_item_amount">213 920 ₽</p>
      </div>
      <div class="balance_item">
        <p class="balance_item_title">К выплате</p>
        <p class="balance_item_amount">159 465 ₽</p>
      </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      
    }
  }
}
</script>

<style lang="scss">
    .balance{
        display: flex;
        background: #fff;
        padding: 18px 30px;
        &_item{
            padding-right: 22px;
            &_title{
                font-family: 'Roboto';
                font-size: 13px;
                line-height: 19px;
                color: #7D7D7D;
                margin: 0;
            }
            &_amount{
                font-family: 'Rubik';
                font-size: 19px;
                line-height: 26px;
                color: #262626;
                margin: 0;
            }
        }
    }
    
</style>
