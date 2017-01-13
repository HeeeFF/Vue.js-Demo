<template>
<div class="ratings">
	<ul>
		<li class="rating-item" v-for="rating in ratings">
			<div class="rating-left">
				<img :src="rating.avatar">
			</div>
			<div class="rating-right">
				<span class="rating-name">
					{{rating.username}}
				</span>
				<span class="rating-deli">
					{{rating.deliveryTime}}分钟送达
				</span>
				<p class="rating-text">
					{{rating.text}}
				</p>
				<span class="rating-rec"  v-for="item in rating.recommend">
					{{item}}
				</span>
			</div>			
		</li>				
	</ul>
</div>
</template>

<script type="text/ecmascript-6">
export default {
  data() {
    return {
      ratings: {}
    };
  },
    created() {
      this.$http.get('/api/ratings?id=' + this.ratings.id).then((response) => {
        response = response.body;
        if (response.errno === 0) {
          this.ratings = Object.assign({}, this.ratings, response.data);
        }
      });
    },
};
</script>

<style>
.ratings {
	margin-bottom: 48px;
}
.rating-item {
	display: flex;
	margin: 0 18px;
	padding: 18px 0;
	border-bottom: 1px solid #d9dde1;
}
.rating-left {
	flex: 0,0,56px;
}
.rating-right {
	flex: 1;
}
.rating-left img {
	margin: 0 12px 0 0;
	width: 28px;
	border-radius: 50%;
}
.rating-name {
	font-size: 10px;
	color: rgb(7,17,27);
	line-height: 12px;

}
.rating-deli {
	font-size: 10px;
	font-weight: 200;
	color: rgb(147,153,159);
	line-height: 24px;
}
.rating-score {
	font-size: 24px;
	color: rgb(255,153,0);
	line-height: 28px;
}
.rating-text {
	font-size: 12px;
	color: rgb(7,17,27);
	line-height: 18px;
	margin-bottom: 4px;
}
.rating-rec {
	display: inline-block;
	margin-right: 8px;
	font-size: 9px;
	color: rgb(147,153,159);
	line-height: 16px;
	border: 1px solid rgb(147,153,159);
	border-radius: 2px;
}
</style>
