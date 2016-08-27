<template lang="pug">
  div.cart(@click='onClickMe')
    header
      div.fl
        i.fa.fa-reorder
      div.fr
        i.fa.fa-close
        i.fa.fa-tag
      div.header-title
        span Your Cart
      div.clr
    section(v-bind:class="{on: cartOn}")
      ul.items
        li(v-for="cartItem in cartItems").item-holder
          div.item-holder-wrapper
            div.item-pic.fl
              div.figure-wrapper
                figure(v-bind:style="cartItem.pic")
            div.item-count.fr
              div.input-wrapper.fl
                input(type='text')
              div.count-wrapper.fl
                p.count-plus
                  i.fa.fa-angle-up
                p.count-minus
                  i.fa.fa-angle-down
              div.clr
            div.item-info
              p.item-title {{ cartItem.title }}
              div.item-size
                span Size:
                span.size {{ cartItem.size }}
              div.item-price
                span $
                span.price {{ cartItem.price }}
            div.clr
      div.total
        span $
        span.total-price 327,00
      div.checkout
        a(href="#") PROCEED TO CHECKOUT
</template>

<script>
  import touch from '../assets/js/lib/touch-0.2.14.min.js'
  export default {
    name: 'Cart',
    data () {
      return {
        // 购物车
        cartItems: [
          { title: 'Muffin Dress', size: 'S', price: '25,00', pic: 'background-image:url(src/assets/images/product-05.jpg)'},
          { title: 'Gorgeus Red Cap', size: '7', price: '112,00', pic: 'background-image:url(src/assets/images/product-05.jpg)'},
          { title: 'Black Trainers', size: '9.5', price: '78,00', pic: 'background-image:url(src/assets/images/product-05.jpg)'}
        ],
        cartOn: false
      }
    },
    props: [''],
    methods: {
      onClickMe: function () {
        this.$emit('child-tell', this.cartOn);
      }
    }
    // ready () {
    //   this.$nextTick(()=>{
    //
    //     // 点击购物车图标，出现购物车
    //     $('.fa-shopping-cart').click(function () {
    //       // $('.cart header').css('display', 'block');
    //       $('.cart section').css({
    //         'display': 'block',
    //         'top': 50+'px'
    //       });
    //     });
    //
    //     // 点击close，关闭购物车
    //     $('.cart .fa-close').click(function () {
    //       // $('.cart header').css('display', 'none');
    //       $('.cart section').css({
    //         'top': -$('.cart section').height()+'px'
    //       })
    //     });
    //
    //   })
    // }
  }
</script>

<style lang="sass">
  // Variables
  $themecolor: #67b0d6;
  $lightorange: #f6846a;
  $darkgrey: #a6a6ad;
  $submenugrey: #eaebeb;
  $lightblack: #3a4144;
  $lightwhite: #f8f8f8;
  $menuicon: #38474f;

  /* 购物车 */
  .cart {

    position: fixed;
    z-index: 10;
    top: 0;
    width: 100%;
    background: $lightorange;

    & header.on {
      display: block;
    }
    & section.on {
      display: block;
      top: 50px;
    }
    /* 标题 */
    & header {

      display:none;
      height: 50px;
      line-height: 50px;

      & .fl, & .fr {
        width: 70px;
        font-size: 1.5rem;
        text-align: center;
        color: $menuicon;
      }
      & .fr i {
        width: 50%;
      }
      & .fr i.fa-close {
        color: $lightwhite;
      }
      & .header-title {
        margin: 0 70px;
        color: white;
      }
    }
    /* 主体*/
    & section {
      display: none;
      position: absolute;
      background: inherit;
      width: 100%;
      transition: all .3s ease-out;
    }

    /* 选购商品 */
    & .items {
      padding: 1rem;

      & .item-holder {
        margin-bottom: 1rem;
        padding: .5rem;
        background: $lightwhite;
        box-shadow: 0px 2px 2px rgba(0,0,0,.2);

        & .item-pic, & .fr {
          width: 60px;
        }

        /* 商品缩略图 */
        & .figure-wrapper {
          padding: .5rem;

          & figure {
            position: relative;
            width: 100%;
            height: 0;
            overflow: hidden;
            margin: 0;
            padding-bottom: 100%;
            background-position: center;
            background-repeat: no-repeat;
            background-size: cover;
            border-radius: 50%;
            box-shadow: 0px 2px 2px rgba(0,0,0,.5);
          }
        }
        /* 商品信息 */
        & .item-info {
          margin: 0 60px;

          & .item-title {
            text-shadow: 1px 1px 1px rgba(0,0,0,.2);
          }
          & .item-size, & .item-price {
            color: $darkgrey;
          }
          & .item-size {
            font-size: .5rem;
          }
          & .item-price {
            margin-top: 1rem;
          }
        }
        /* 商品数量控制 */
        & .item-count {
          padding: 1rem 0;

          & .input-wrapper, & .count-wrapper {
            width: 50%;
          }
          & .input-wrapper {
            & input {
              margin-top: .4rem;
              width: 100%;
              height: 2rem;
              text-align: center;
              background: transparent;
            }
          }
        }
      }
    }

    /* 总价 */
    & .total {
      padding-bottom: 1rem;
      color:white;
      text-align: center;
    }

    /* 结账link */
    & .checkout {
      text-align: center;
      padding-top: 1rem;
      padding-bottom: 2rem;
      & a {
        padding: 1rem 2rem;
        background: $lightblack;
        color: white;
        font-size: .8rem;
        border-radius: 2px;
        box-shadow: 1px 1px 2px rgba(0,0,0,.2);
      }
    }

  }
</style>
