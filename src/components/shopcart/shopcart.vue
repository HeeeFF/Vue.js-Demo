<template>
	<div class="shopcart">
		<div class="shop-content">
			<div class="left">
				<div class="logo-warp">
					<div class="logo">
						<img src="cart_fill.svg">
					</div>
				</div>
				<div class="price">0元</div>
				<div class="desc">另需配送费{{deliveryPrice}}元</div>
			</div>
			<div class="right">
				<div class="pay">￥{{minPrice}}起送</div>
			</div>
		</div>
	</div>
</template>

<script type="text/ecmascript-6">
export default {
	props: {
		deliveryPrice: {
		type: Number
		},
		minPrice: {
		type: Number
		}
	},
}
</script>

<style>
.shopcart {
	position: fixed;
	left: 0;
	bottom: 0;
	z-index: 50;
	width: 100%;
	height: 48px;
}
.shop-content {
	display: flex;
	background: #141d27;
	color: rgba(255,255,255,0.1);
}
.shop-content .left {	
	flex: 1;
}
.shop-content .right {
	flex: 0 0 105px;
	width: 105px;
}
.logo-warp {
	display: inline-block;
	position: relative;
	top: -10px;
	margin: 0 12px;
	padding: 6px;
	width: 56px;
	height: 56px;
	box-sizing: border-box;
	border-radius: 50%;
	background: #141d27;
}
.logo {
	width: 100%;
	height: 100%;
	border-radius: 50%;
	background: #2b343c;
	text-align: center;
}
.logo img {
	height: 40px;
	color: #80858a;
}
.desc {
	display: inline-block;
	vertical-align: top;
	margin: 12px 0 0 12px;
	line-height: 24px;
	font-size: 10px;
}
.price {
	display: inline-block;
	height: 26px;
	vertical-align: top;
	margin-top: 12px;
	line-height: 24px;
	padding-right: 12px;
	border-right: 1px solid rgba(255,255,255,0.1);
	font-size: 10px;
	font-size: 16px;
	font-weight: 700;
}
.pay {
	height: 48px;
	line-height: 48px;
	text-align: center;
	font-size: 16px;
	font-weight: 700;
	background: #2b333b;
}
</style>
