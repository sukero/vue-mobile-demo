<template lang="pug">
  header.topbar
    div.fl
      i.fa.fa-reorder
    div.fr
      i.fa.fa-shopping-cart(@child-tell='listentomyboy')
      i.fa.fa-tag
    div.topbar-title
      span eCommerce
    div.clr
  // 购物车
  Cart(v-bind:class="{on: cartOn}")
</template>

<script>
  import Cart from './Cart.vue'
  export default {
    name: 'Topbar',
    components: {
      Cart
    },
    data () {
      return {
        cartOn: false
      }
    },
    methods: {
      listentomyboy: function () {
        this.cartOn = !this.cartOn;

        console.log(this.cartOn);
      }
    }
  }
</script>

<style lang="sass">
  @import "../assets/scss/reset.scss";
  // Variables SCSS变量
  $themecolor: #67b0d6;
  $menuicon: #38474f;
  .topbar {
    width: 100%;
    height: 50px;
    line-height: 50px;
    text-align: center;
    color: white;
    background: $themecolor;

    & .fl, & .fr {
      width: 70px;
      font-size: 1.5rem;
      color: $menuicon;
    }
    & .fr i {
      width: 50%;
    }
    & .topbar-title {
      margin: 0 70px;
      text-align: left;
    }
  }
</style>
