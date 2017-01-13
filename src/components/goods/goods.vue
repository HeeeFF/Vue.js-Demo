<template>
	<div class="goods">
		<div class="menu" v-el:menu>
			<ul>
				<li class="good-item" v-for="item in goods">
					<span class="good-text">
						{{item.name}}
					</span>
				</li>				
			</ul>
		</div>
		<div class="foods" v-el:food>
			<ul>
				<li v-for="item in goods" class="food-list">
					<h1 class="title">{{item.name}}</h1>
					<ul>
						<li class="item-food" v-for="food in item.foods">
							<div class="food-ico">
								<img :src="food.icon">
							</div>
							<div class="food-section">
								<div class="food-con">
									<h2>{{food.name}}</h2>
									<p>{{food.description}}</p>
								</div>
								<div class="food-rating">
									<span>月售:{{food.sellCount}}</span>
									<span>好评率:{{food.rating}}</span>
								</div>
								<div class="food-price">
									￥<span>{{food.price}}</span>
								</div>
							</div>
						</li>
					</ul>
				</li>
			</ul>
		</div>	
	</div>
</template>

<script  type="text/ecmascript-6">
import BScroll from 'better-scroll'

export default {
    data() {
       return {
        	goods: [],
        };
    },
    created() {
      this.$http.get('/api/goods?id=' + this.goods.id).then((response) => {
        response = response.body;
        if (response.errno === 0) {
          this.goods = Object.assign({}, this.goods, response.data);
          this.$nextTick(() => {
          	this.initScroll();
          });
        }
      });
    },
    methods: {
    	initScroll() {
    		this.menuScroll = new BScroll(this.$els.menu, {});
    		this.foodScroll = new BScroll(this.$els.food, {
    			probeType: 3
    		});
    	},
    },
};
</script>

<style>
.goods {
	display: flex;
	position: absolute;
	width: 100%;
	top: 176px;
	bottom: 46px;
	overflow: hidden;
}
.menu {
	flex: 0 0 80px;
	width: 80px;
	background: #f3f5f7;
}
.foods {
	flex: 1;
}
.good-item {
	display: table;
	height: 54px;
	width: 56px;
	line-height: 14px;
	padding: 0 12px;
}
.good-text {
	display: table-cell;
	width: 56px;
	vertical-align: middle;
	text-align: center;
	border-bottom: 1px solid #d9dde1;
	font-size: 12px;
	color: #000;
	font-weight: 200;
	padding: 0;
}
.food-list .title {
	height: 26px;
	width: 100%;
	background: #f3f5f7;
	border-left: 3px solid #d9dde1;
	color: rgb(147,153,159);
	text-indent: 14px;
	font-size: 12px;
	line-height: 26px;
}
.item-food {
	display: flex;
	border: 18px;
	border-bottom: 1px solid #f3f5f7;

}
.food-ico {
	flex: 0 0 80px;
	width: 92px;
	padding: 18px 0 0 18px;
}
.food-ico img {
	width: 64px;
	border-radius: 2px;
}
.food-section {
	flex: 1;
	padding-top: 20px;
}
.food-con h2 {
	margin-bottom: 8px;
	font-size: 14px;
	color: rgb(7,17,27);
	line-height: 14px;
}
{}
.food-rating span, .food-con p {
	display: inline-block;
	margin-bottom: 8px;
	font-size: 10px;
	color: rgb(147,153,159);
	line-height: 10px;
}
.food-price {
	font-size: 12px;
	color: red;
	font-weight: 700;
	line-height: 24px;
}
.food-price span {
	font-size: 18px;
	font-weight: bold;
}
shopcart {
	position: absolute;
	left: 0;
	bottom: 0;
}
</style>
