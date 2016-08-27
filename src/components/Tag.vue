<template lang="pug">
  div.tag(v-if="isOn", v-bind:class="{on: isOn}")
    ul.sorts
      li(v-for="sort in sorts").sort.fl
        span {{ sort.title }}
      div.clr
</template>

<script>
  import touch from '../assets/js/lib/touch-0.2.14.min.js'
  export default {
    name: 'Tag',
    data () {
      return {
        // 标签分类
        sorts: [
          { title: 'Advice' },
          { title: 'Recent' },
          { title: 'Popular'}
        ]
      }
    },
    methods: {
      toggle: function () {
        this.isOn = !this.isOn;
        $('.fa-tag').css('color', 'white');
      }
    },
    ready () {
      this.$nextTick(()=>{

        /* ------ 购物车 ------ */

        // // 点击购物车图标，出现购物车
        // $('.fa-shopping-cart').click(function () {
        //
        //   $('.cart').css('display', 'block');
        //   $('.cart header').addClass('on');
        //   $('.cart section').addClass('on');
        //
        //   // 标签切换购物车，隐藏标签section
        //   $('.fa-tag').removeClass('on');
        //   $('.tag').removeClass('on');
        //
        // });
        //
        // // 点击close，关闭购物车
        // $('.cart .fa-close').click(function () {
        //   $('.cart header').removeClass('on');
        //   $('.cart section').removeClass('on');
        //   $('.cart section').css({
        //     'top': -$('.cart section').height()+'px'
        //   })
        // });

        /* ------ 标签分类 ------ */

        // 点击tag图标，出现标签分类
        // $('.fa-tag').click(function () {
        //
        //   $('.fa-tag').toggleClass('on');
        //   $('.tag').toggleClass('on');
        //
        //   // 购物车->切换->标签
        //   $('.cart').css('display', 'none');
        // });
        //
        // // 默认选择
        // $('.tag .sort:last').addClass('on');
        //
        // // 被选中的项
        // $('.tag .sort').click(function () {
        //   $(this).addClass('on');
        //   $(this).siblings().removeClass('on');
        // });
      })
    }
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

  /* on状态下的tag图标 */
  .fa-tag.on {
    color: $lightwhite;
  }

  /* 分类 */
  .tag {

    display: none;
    position: fixed;
    width: 100%;
    background: $themecolor;
    transition: all .3s ease-out;

    &.on {
      display: block;
      top: 50px;
      z-index: 10;
    }
    /* 主体*/
    & section {

      position: absolute;
      background: inherit;
      width: 100%;
    }
    & .sorts {
      padding: .5rem;
    }
    & .sort {
      padding: 1rem .5rem;
      width: 33.3%;
      font-size: .8rem;
      text-align: center;

      &.on {
        background: $lightwhite;
        box-shadow: 1px 1px 2px rgba(0,0,0,.2);
        border-radius: 3px;
      }
    }

  }
</style>
