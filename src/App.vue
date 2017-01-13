<template>
  <div>
    <v-header :seller="seller"></v-header>
    <div class="tab border-1px">
      <div class="tab-item" v-link="{path:'/goods'}">
        <a>商品</a>
      </div>
      <div class="tab-item" v-link="{path:'/ratings'}">
        <a>评论</a>
      </div>
    </div>
    <router-view transition="move"></router-view>
    <shopcart :delivery-price="seller.deliveryPrice" :min-price="seller.minPrice" ></shopcart>
  </div>
</template>

<script type="text/ecmascript-6">
import header from './components/header/header.vue'
import shopcart from 'components/shopcart/shopcart.vue'

export default {
  data() {
    return {
      seller: {}
    };
  },
    created() {
      this.$http.get('/api/seller?id=' + this.seller.id).then((response) => {
        response = response.body;
        if (response.errno === 0) {
          this.seller = Object.assign({}, this.seller, response.data);
        }
      });
    },
  components: {
  	'v-header': header,
    shopcart
  }
};
</script>

<style>
.tab {
  display: flex;
  height: 40px;
  width: 100%
}
.tab-item {
  flex: 1;
  line-height: 40px;
  text-align: center;
}
.active a {
  color: rgb(0,160,220);
}
.active {
  border-bottom: 2px solid rgb(0,160,220);
}
.move-transition {
  transition: all 0.3s linear;
  transform: translate3d(0,0,0);
}
.move-enter, .move-leave {
  transform: translate3d(100%,0,0);
}
</style>