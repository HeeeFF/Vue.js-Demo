<template>
	<div clsss="header">
		<div class="main"  @click="showDetail">
			<div class="img" >
				<img :src="seller.avatar">
			</div>
			<div class="content">
				<div class="titie">
					<span><img src="brand@2x.png" height="18" width="30"></span>
					<span class="name">{{seller.name}}</span>
				</div>
				<div class="description">
					<span>{{seller.description}}{{seller.deliveryTime}}分钟送达</span>
				</div>
				<div v-if="seller.supports" class="support" >
					<span><img src="decrease_1@2x.png" height="12" width="12"></span>
					<span >{{seller.supports[0].description}}</span>
				</div>
			</div> 
		</div>
		<div v-if="seller.supports" class="activity" @click="showDetail">
			<span class="ico"><img src="bulletin@2x.png" height="12" width="22"></span>
			<span>{{seller.supports[3].description}}</span>
		</div>
		<div class="background">
			<img :src="seller.avatar" height="100%" width="100%">
		</div>
		<div v-show="detailShow" class="detil"  @click="hideDetail" transition="fade" >
			<h1>{{seller.name}}</h1>
			<div class="meg">
				<div class="line"></div>
				<div class="text">优惠信息</div>
				<div class="line"></div>
			</div>
			<ul class="tips" v-if="seller.supports">
				<li>
					<span><img src="decrease_1@2x.png" height="12" width="12"></span>
					<span >{{seller.supports[2].description}}</span>
				</li>
				<li>
					<span><img src="discount_1@2x.png" height="12" width="12"></span>
					<span >{{seller.supports[1].description}}</span>
				</li>
				<li>
					<span><img src="guarantee_1@2x.png" height="12" width="12"></span>
					<span >{{seller.supports[3].description}}</span>
				</li>
			</ul>
			<div class="meg">
				<div class="line"></div>
				<div class="text">商家公告</div>
				<div class="line"></div>
			</div>
			<div class="bulletin">{{seller.bulletin}}</div>
		</div>
	</div>
</template>

<script type="text/ecmascript-6">
  export default {
    props: {
      seller: {
        type: Object
      }
    },
    data() {
      return {
        detailShow: false
      };
    },
    methods: {
      showDetail() {
        this.detailShow = true;
      },
      hideDetail() {
        this.detailShow = false;
      }
    },
  };
</script>
	
<style>
.main {
	color: #fff;
	background: rgba(7,17,27,0.2);
}
.img {
	display: inline-block;
	margin: 24px 16px 18px 24px;
}
.img img {
	height: 64px;
	width: 64px;
}
.content {
	display: inline-block;
	margin-bottom: 18px;
}
.name {
	display: inline-block;
	margin-bottom: 8px;
	font-size: 18px;
	font-weight: bold;
	line-height: 18px;
}
.description {
	display: block;
	margin-bottom: 10px;
	font-size: 12px;
	font-weight: 200;
	line-height: 12px;
}
.support {
	font-size: 14px;
	font-weight: 200;
	line-height: 14px;
}
.activity {
	height: 28px;
	background: rgba(7,17,27,0.5); 
	color: #fff;
	font-size: 10px;

}
.activity .ico {
	display: inline-block;
	margin: 8px 4px 8px 12px;
}
.background {
	position: absolute;
	top: 0;
	left: 0;
	z-index: -1;
	width: 100%;
	height: 132px;
	filter: blur(10px);
}
.detil {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background: rgba(7,17,27,0.8); 
	overflow: auto;
	color: #fff;
	transition: all 1s;
	backdrop-filter: blur(10px);
	z-index: 100;
}
.fade-transition {
	opacity: 1;
	background: rgba(7,17,27,0.8);
}
.fade-enter, .fade-leave {
	opacity: 0;
	background: rgba(7,17,27,0); 
}
.detil h1 {
	font-size: 16px;
	line-height: 16px;
	font-weight: 700;
	margin: 64px;
	text-align: center;
}
.meg {
	display: flex;
	width: 80%;
	margin: 30px auto 24px auto; 
}
.line {
	flex: 1;
	position: relative;
	top: -6px;
	border-bottom: 1px solid rgba(255,255,255,0.2);
}
.text {
	font-size: 14px;
	line-height: 14px;
	font-weight: 700;	
	padding: 0 12px;
}
.tips {
	width: 80%;
	margin: 0 auto;
}
.tips li {
	padding-bottom: 12px;
	font-size: 12px;
	font-weight: 200;
	line-height: 12px;
}
.bulletin {
	width: 80%;
	margin: 0 auto;
	font-size: 12px;
	font-weight: 200;
	line-height: 24px;
}
</style>
