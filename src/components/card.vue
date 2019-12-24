<template>
  <div class="card">
      <div class="card_left">
          <h3 class="card_title">{{data.title}}</h3>
          <p class="card_desc">{{data.description}}</p>
      </div>
      <div class="card_right">
        <div class="card_right_block card_right_promocode_wrapper">
            <p class="card_right_label">ПРОМОКОД</p>
            <input type="text" class="card_right_promocode" readonly :value="data.promocode" v-on:click="copyToClip">
        </div>
        <div class="card_right_block">
            <a :href="data.link" target="_blank" class="card_button">Получить бонус</a>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  props: ['data'],
  data () {
    return {
      
    }
  },
  methods: {
    copyToClip: function(e){
        let val = e.target;
        val.select();
        val.setSelectionRange(0, 99999)
        document.execCommand("copy");
        alert("Copied the text: " + val.value);
    }
  }
}
</script>

<style lang="scss">

    .card{
        background: #fff;
        border-radius: 6px;
        border: 1px solid #E2E5EC;
        display: flex;
        padding: 26px 32px;
        margin-top: 24px;
        &_left{
            width: 42%;
        }
        &_title{
            font-size: 29px;
            line-height: 42px;
            color: #000;
            margin: 0;
            margin-bottom: 5px;
        }
        &_button{
            font-size: 19px;
            line-height: 28px;
            color: #FFFFFF;
            background: #0085FF;
            border-radius: 4px;
            width: 100%;
            display: block;
            text-align: center;
            text-decoration: none;
            padding: 12px 0;
        }
        &_desc{
            font-size: 15px;
            line-height: 22px;
            color: #7D7D7D;
            margin: 0;
        }
        &_right{
            display: flex;
            width: 58%;
            &_block{
                width: 50%;
                    display: flex;
                    flex-direction: column;
                    justify-content: flex-end;
                &:last-child{
                    padding-left: 24px;
                }
            }
            &_label{
                font-size: 11px;
                line-height: 16px;
                margin: 0;
                margin-bottom: 7px;
                color: #7D7D7D;
            }
            &_promocode{
                width: 100%;
                font-size: 15px;
                line-height: 22px;
                padding: 15px 17px 11px 17px;
                color: #262626;
                position: relative;
                box-sizing: border-box;
            }
            
        }
        
    }
    .card_right_promocode_wrapper{
        position: relative;
        &:after{
            content: '';
            display: block;
            width: 16px;
            height: 16px;
            position: absolute;
            right: 12px;
            top: 42px;
            background: url('../assets/icon.svg') no-repeat;
        }
    }
</style>
