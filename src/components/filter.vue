<template>
  <div class="filterSearch">
      <div class="filterSearch_left">
          <p class="filterSearch_left_title">Фильтр</p>
          <input type="text" class="filterSearch_input" @input="change" v-model="text">
      </div>
      <div class="filterSearch_right">
          <button type="button" class="filterSearch_right_button" v-on:click="resetCard">Сбросить</button>
      </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      text: ''
    }
  },
  methods: {
    change () {
        this.$emit('change', {
            text: this.text
        })
    },
    resetCard() {
        this.text = '';
        this.$emit('reset', {})
    }
  },
}
</script>

<style lang="scss">
    .filterSearch{
        display: flex;
        &_left{
            &_title{
                font-size: 11px;
                line-height: 16px;
                margin: 0;
                margin-bottom: 2px;
                color: #7D7D7D;
            }
        }
        &_right{
            display: flex;
            flex-direction: column;
            justify-content: flex-end;
            padding-left: 8px;
            &_button{
                font-size: 19px;
                line-height: 28px;
                color: #262626;
                padding: 9px 33px;
                border: 1px solid #CFD2D9;
                background: #F5F7FA;
                cursor: pointer;
            }
        }
        &_input{
            background: #FFFFFF;
            border: 1px solid #2F80ED;
            font-family: 'Roboto';
            font-size: 15px;
            border-radius: 4px;
            box-sizing: border-box;
            padding: 17px 15px 11px 15px;
            width: 300px;
            outline: none;
        }
    }
</style>
