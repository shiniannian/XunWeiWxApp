<template>
	<view class="content">
		<view class="top-bar">
			<view class="top-bar-left">
				所有店铺（餐饮均在3、4层）
				<text class="top-title">  </text>
				
			</view>
			<view class="top-bar-right">
				
				<view class="add"> <image src="../../static/add.png"></image> </view>
				<view class="search"> <image src="../../static/atlas-search.png"></image> </view>
			</view>
		</view>
		<view class="main">
			<view class="news">
				<view class="news_item" @tap="onClick(news)" v-for="news in newsList">
					<view class="news_item_l">
						<!--<text class="tip">1</text>-->
						<image :src="news.image"></image>
					</view>
					<view class="news_item_r">
						<view class="upper">
							<view class="name">{{news.title}}</view>
							<view class="time">{{news.time}}</view>
						</view>
						<view class="person">{{news.title_short}}</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>

export default {
	data() {
		return{
			newsList:[
				{"title":"美食每刻","title_short":"当前上座率：30%（有包厢）","image":"../../static/shop/1.png","time":"3F01","content":"店铺详情"},
				{"title":"家味道","title_short":"当前上座率：50%（有包厢）","image":"../../static/shop/2.png","time":"3F04","content":"店铺详情"},
				{"title":"稿定小吃","title_short":"当前上座率：40%（有包厢）","image":"../../static/shop/3.png","time":"3F03","content":"店铺详情"},
				{"title":"大食尚","title_short":"当前上座率：70%（有包厢）","image":"../../static/shop/4.png","time":"3F05","content":"店铺详情"},
				{"title":"小食神","title_short":"当前上座率：60%（有包厢）","image":"../../static/shop/5.png","time":"3F02","content":"店铺详情"},
				{"title":"美食点播","title_short":"当前上座率：90%（有包厢）","image":"../../static/shop/6.png","time":"4F01","content":"店铺详情"},
				{"title":"食悦轩","title_short":"当前上座率：20%（有包厢）","image":"../../static/shop/7.png","time":"4F04","content":"店铺详情"},
				{"title":"品味","title_short":"当前上座率：10%（有包厢）","image":"../../static/shop/8.png","time":"4F05","content":"店铺详情"},
				{"title":"湘厨","title_short":"当前上座率：80%（有包厢）","image":"../../static/shop/9.png","time":"4F03","content":"店铺详情"},
			],
			//newsList:[]
		}
	},
	onLoad() {
		//this.getNewsList();
	},
	methods: {
		onClick(news) {
			uni.navigateTo({url: "news_details?news=" + JSON.stringify(news)})
		},
		
		getNewsList()
		{
			uni.request({
				url:'http://42.193.114.253:8081/interfaceTwo',
					success: (res) => {
					        //console.log(res.data.data);
					        this.newsList = res.data.data;
						}
			});
		}
	}
}
</script>

<style lang="scss">
page {
	  background-color: $main-color;
	 }
	 
	.content{
		display: flex;
		flex-direction: column;
		//align-items: center;
		justify-content: center;
	}
	.top-bar{
		position: fixed;
		z-index: 1001;
		top: 0;
		left: 0;
		width: 100%;
		height: 70rpx;
		box-sizing: border-box;
		background-color: $main-color;
		box-shadow: 0rpx 1rpx 0rpx 0rpx rgba(0,0,0,0.1);
		padding-left: 32rpx;
		padding-right: 32rpx;
		.top-bar-left{
			float:left;
			margin-top: 10rpx;
			margin: 10rpx;
			font-weight:540;
			width: auto;
			color: $text-color;
			opacity:0.83;
			
			.top-title{
				color: rgba(255,93,91,1);
				margin-left: 30rpx;
				margin-right: 30rpx;
			}
		}
		.top-bar-right{
			float: right;
			.search{
				width: 30rpx;
				height: 30rpx;
				display: inline-block;
				margin-right: 20rpx;
			}
			.add{
				width: 30rpx;
				height: 30rpx;
				display: inline-block;
				margin-right: 45rpx;
			}
			image{
				padding: 10rpx 0 0 10rpx;
				width: 52rpx;
				height: 52rpx;
			}
		}
	}
	.main{
		padding: 70rpx 32rpx 0;
	}
	.news{
		width: 100%;
		.news_item{
		height: 96rpx;
		padding: 16rpx 0;
		border-bottom: 1rpx solid #484D5B;
		.news_item_l{
			position:relative;
			float: left;
			image{
				width: 96rpx;
			 	height: 96rpx;
				border-radius: 50%;
			}
			.tip{
				position: absolute;
				z-index: 100;
				top: -6rpx;
				left: 68rpx;
				min-width: 36rpx;
				height: 36rpx;
				background: rgba(255,93,91,1);
				border-radius: 18rpx;
				line-height: 36rpx;
				text-align: center;
				color: white;
			}
		}
		.news_item_r{
			padding-left: 128rpx;
			//width: 100%;
			.upper{
				height: 50rpx;
				.name{
					float: left;
					font-size: 28rpx;
					font-weight: 400;
					//color:rgba(39,40,50,1);
					font-weight:540;
					line-height: 50rpx;
					
					color: $text-color;
				}
				.time{
					float: right;
					font-size: 24rpx;
					color: $text-color;
					line-height: 50rpx;
					opacity:0.8;
				}
			}
		}
		.person{
			font-size: 24rpx;
			color: $text-color;
			opacity:0.8;
			line-height: 40rpx;
		}
	 }
    }

</style>
