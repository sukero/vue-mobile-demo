<template lang="pug">
  // 主页
  div.swiper-container
    div.swiper-wrapper
      div.swiper-wrapper
        div.swiper-slide
          img(src="../assets/images/slide-01.jpg")
          a(href="#").slide-link DISCOVER
        div.swiper-slide
          img(src="../assets/images/slide-01.jpg")
        div.swiper-slide
          img(src="../assets/images/slide-01.jpg")
  div.search
    div.search-wrapper
      div.fl
        i.fa.fa-search
      div.input-wrapper
        input(type="search",placeholder="Search a Item...")
      div.clr
  article.product-module
    header OUR POPULAR PRODUCTS
    section.product-section
      ul
        li(v-for="product in products").fl
          div.product
            div.img-wrapper
              img(v-bind:src="product.url")
            div.info-wrapper
              p {{ product.name }}
              p.price {{ product.price }}
        div.clr
  div.loading
    div.loading-wrapper
      i.fa.fa-refresh
  div.view-all
    div.view-all-wrapper
      a(href="#") View all Items
  // 左侧滑菜单
  <Sidebar></Sidebar>
  // 购物车
  <Cart></Cart>
  // 标签分类
  <Tag></Tag>
</template>

<script>
  import swiper from '../assets/js/lib/swiper.min.js'
  import Sidebar from '../components/Sidebar.vue'
  import Cart from '../components/Cart.vue'
  import Tag from '../components/Tag.vue'

  export default {
    components: {
      Sidebar,
      Cart,
      Tag
    },
    data() {
      return {
        products: [
          { name: 'Pink Shirt', url: 'src/assets/images/product-01.jpg', price: '$ 249.00' },
          { name: 'Pink Shirt', url: 'src/assets/images/product-02.jpg', price: '$ 50.00' },
          { name: 'Pink Shirt', url: 'src/assets/images/product-03.jpg', price: '$ 181.99' },
          { name: 'Pink Shirt', url: 'src/assets/images/product-04.jpg', price: '$ 372.00' }
        ]
      }
    },
    ready () {

      this.$nextTick(()=>{

        // 轮播图
        let mySwiper = new Swiper('.swiper-container', {
          loop: true
        })
      })
    }
  }
</script>

<style lang="sass" scoped>
  @import "../assets/css/lib/swiper.min.css";

  // Variables
  $themecolor: #67b0d6;
  $lightorange: #f6846a;
  $darkgrey: #a6a6ad;
  $submenugrey: #eaebeb;
  $lightblack: #3a4144;
  $lightwhite: #f8f8f8;
  $menuicon: #38474f;

  /* 轮播图 */
  .swiper-slide {
    position: relative;
  }
  .swiper-slide img {
    width: 100%;
  }
  .swiper-slide a.slide-link {
    display: block;
    position: absolute;
    right: 50px;
    bottom: 20px;
    padding: .5rem;
    font-size: .5rem;
    color: white;
    background: $lightorange;
    border-radius: 5px;
  }

  /* 搜索框 */
  .search {
    padding: 1rem 2rem;
    color: $darkgrey;

    & .search-wrapper {
      height: 40px;
      line-height: 40px;
      background: white;
      box-shadow: 0px 2px 2px rgba(0, 0, 0, .3);
    }
    & .fl {
      width: 50px;
      text-align: center;
    }
    & .input-wrapper {
      margin-left: 50px;
    }
  }

  /* 商品 */
  .product-module header {
    padding: 1rem;
    margin: 1rem auto;
    text-align: center;
    font-weight: bold;
    position: relative;

    &::before, &::after {
      position: absolute;
      content: '';
      top: 0;
      left: 50%;
      transform: translateX(-50%);
      width: 80px;
      border-bottom: 3px solid $darkgrey;
      color: $darkgrey;
    }
    &::after {
      bottom: 0;
    }
  }
  .product-section {
    padding: .5rem;

    & li {
      width: 50%;
      padding: .5rem;
    }
  }
  .product {
    background: $lightwhite;
    text-align: center;
    border-radius: 10px;
    box-shadow: 0px 2px 2px rgba(0, 0, 0, .3);

    & img {
      width: 90%;
    }

    & .info-wrapper {
      padding: .5rem 0;
    }
    & .price {
      color: $darkgrey;
    }
  }

  /* 下拉更新提示 */
  .loading {
    text-align: center;
    padding: 1rem 0;

    & .loading-wrapper {
      position: relative;
      display: inline-block;
      width: 50px;
      height: 50px;
      line-height: 50px;
      border-radius: 50%;
      color: white;
      background: $themecolor;
      box-shadow: 1px 1px 2px rgba(0, 0, 0, .3);

      & i {
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        font-size: 2rem;
      }
    }
  }

  /* 查看全部 */
  .view-all {
    text-align: center;
    margin: 1rem 0;

    & .view-all-wrapper {
      display: inline-block;
      padding: 1rem 2rem;
    }
    & a {
      padding: 1rem 2rem;
      background: $lightblack;
      border-radius: 5px;
      color: white;
      box-shadow: 1px 1px 3px rgba(0,0,0,.3);
    }
  }
</style>
