<template lang="pug">
aside#sidebar.sidebar
  div.choose-gender
    header You looking for?
    section
      span.fr WOMAN
      span MAN
      div.clr
  div.toggle-menus
    ul
      li(v-for="menu in menus").menu
        input(type='radio', name='radio-accordion', v-bind:id="menu.id")
        label(v-bind:for="menu.id")
          div.fl
            i.fa.fa-map
          div.fr
            i.fa.fa-angle-down
          div.menu-title
            p {{ menu.name }}
        div.sub-menu
          ul
            li {{ menu.subMenus[0] }}
            li {{ menu.subMenus[1] }}
            li {{ menu.subMenus[2] }}
            li {{ menu.subMenus[3] }}
        div.clr
  div.settings
    ul
      li(v-for="setting in settings").setting
        a(href="#")
          div.fl
            i.fa.fa-user
          div.fr
          div.setting-title {{ setting.name }}
          div.clr
</template>

<script>
  import touch from '../assets/js/lib/touch-0.2.14.min.js'
  export default {
    name: 'Sidebar',
    data () {
      return {
        // 左侧滑菜单
        menus: [
          { id:'radio-1', name: 'Clothings', subMenus: ['Skirts', 'Dresses', 'Jackets', 'Pants'] },
          { id:'radio-2', name: 'Shoes', subMenus: ['Sneakers', 'Sandals', 'Boots', 'Slippers'] },
          { id:'radio-3', name: 'Sports', subMenus: ['Coats', 'Coats', 'Coats', 'Coats'] },
          { id:'radio-4', name: 'Bags & Accessory', subMenus: ['Purses', 'Rings', 'Necklaces', 'Hats'] }
        ],
        // 左侧滑菜单的选项
        settings: [
          { name: 'Account' },
          { name: 'Setting' }
        ]
      }
    },
    ready () {
      this.$nextTick(()=>{

        // 左侧滑菜单

        /* 点击按钮滑出菜单 + 遮罩*/
        $('.fa-reorder').click(function () {

          /* 滑出菜单 */
          $('.sidebar').css('left', 0);

          // 隐藏购物车和标签分类
          $('.cart').hide();
          $('.tag').removeClass('on');
          $('.fa-tag').removeClass('on');

        });

        /* 撤回菜单 */

        var target = document.getElementById("sidebar");
        target.style.webkitTransition = 'all ease 0.2s';

        touch.on(target, 'swipeleft', function(){
          this.style.left = "-80%";
        });

        /* 默认第一个菜单checked */
        $('.menu').eq(0).children(':radio').prop('checked','checked');
        /* 默认第一个菜单的子菜单显示 */
        $('.menu').eq(0).children('.sub-menu').css('display','block');

      })
    }
  }
</script>

<style lang="sass">
  @import "../assets/scss/reset.scss";

  // Variables
  $themecolor: #67b0d6;
  $lightorange: #f6846a;
  $darkgrey: #a6a6ad;
  $submenugrey: #eaebeb;
  $lightblack: #3a4144;
  $lightwhite: #f8f8f8;
  $menuicon: #38474f;

  /* 左侧滑菜单*/
  .sidebar {
    position: fixed;
    left: -80%;
    top: 0;
    z-index: 20;
    width: 80%;
    height: 100%;
    background: white;
    transition: all .6s ease-out;

    /* 选择性别 */
    & .choose-gender {
      padding: 1rem;
      color: white;
      background: #38474f;

      & header {
        padding: 1rem;
        padding-left: 0;
      }
      & section span {
        display: inline-block;
        width: 45%;
        padding: .5rem .8rem;
        font-size: .5rem;
        text-align: center;
        background: #29353a;
      }
    }

    /* 商品类别 */
    & .toggle-menus {

      /* 一级菜单 */
      & .menu {

        & input[type=radio] {
          display: none;
          width: 100%;
          height: 100%;
          &:checked ~ label .fl, &:checked ~ label .fr {
            color: $lightorange;
          }
          &:checked ~ label {
            background: $submenugrey;
          }
        }
        & label {
          display: block;
          height: 40px;
          line-height: 40px;
          background: $lightwhite;
        }
        & .fl, & .fr {
          width: 50px;
          color: $darkgrey;
          text-align: center;
        }
        & .menu-title {
          margin: 0 50px;
          font-size: .8rem;
          text-transform: uppercase;
          transition: all .2s ease-out;
        }
      }

      /* 二级菜单 */
      & .sub-menu {
        padding:0 10px;
        overflow:hidden;
        transition: all .5s ease-out;
        padding-left: 4rem;
        color: $darkgrey;
        background: $submenugrey;

        & li {
          height: 30px;
          line-height: 30px;
          font-size: .8rem;
        }
      }

      & ul li .sub-menu {
        height: 0;
      }
      & [type=radio]:checked ~ label ~ .sub-menu {
        height: 120px;
      }
    }

    /* 选项 */
    & .settings {
      margin-top: 1rem;
      position: relative;

      &::before {
        display: block;
        content: '';
        margin: 0 auto;
        width: 50%;
        height: 3px;
        border-top: 3px solid #cacace;
      }
      & li {
        height: 40px;
        line-height: 40px;
        padding-left: 1rem;
      }
      & a {
        color: black;

        & .fl, & .fr {
          width: 50px;
          color: $darkgrey;
        }
        & .setting-title {
          margin: 0 50px;
          font-size: .8rem;
          text-transform: uppercase;
        }
      }
    }
  }
</style>
