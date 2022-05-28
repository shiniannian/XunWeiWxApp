<template>
<view>
	
<!--
<view class="my_title">
	  
	  <view class="logo">
	    <image class="logo_image" style="width:54rpx;height:60rpx;padding-left: 20rpx;" src="../../static/atlas-sort.png"></image>
	  </view>

	 
	  <view class="atlas-search">
	    <image src="../../static/atlas-search.png" style="width:54rpx;height:60rpx;padding-right: 20rpx;"></image>
	  </view>
</view>

	<view class="atlas-title">
		今日实时榜
	</view>
-->
  <!-- 轮播图 -->
    <view class="bbs-swiper-container">
        <swiper class="bbs-swiper" autoplay="true" circular="true" 
            interval="3000" easing-function="easeOutCubic" 
            :current="swiperCurrent" 
            bindchange="swiperChange">
            <!-- 轮播图图片 -->
            <swiper-item class="bbs-swiper-item" v-for="item in rotationList">
            <!-- 加上widthFix可以使图片自适应 -->
            <image :src="item"></image>
            </swiper-item>
        </swiper>
        <!-- 定制轮播图dots -->
		
		
        <view class="bbs-dots">
            <block v-for="index of rotationList.length" key="index">
            <view class="  index == swiperCurrent ? 'bbs-dots-item bbs-dot-active' : 'bbs-dots-item' "></view>
            </block>
        </view>
    </view>
	
<view class="hot_goods">

	<view class="goods_list">
		<view class="goods_item" v-for="item in goods" :key="item.id" @click="navigator(item.goods_id)">
			<image :src="item.goods_img?
			item.goods_img:'../../static/icon/empty.png'">
			</image>
			<view class="price">
				<text>{{item.goods_top}}</text>
				<text>{{item.goods_name}}</text>
			</view> 
			<view class="name">
				<text>{{item.goods_content}}</text>
			</view>
		</view>
	
	</view> 
</view>

</view>
</template>

<script>
	export default{
		
		data() {
			return {
				navH: 0,
				
				//轮播图
				rotationList:[
				  '../../static/hypermarket/lunbo1.png',
				  '../../static/hypermarket/lunbo2.png',
				 
				  
				],
				swiperCurrent: 0,
				
				goods:[
					{
						"goods_id" : "1" ,
						"goods_img" : "../../static/hypermarket/1.png",
						"goods_top":"L1",
						"goods_content":"美食每刻 1F01\n 家味道 1F04\n 稿定小吃 1F03\n",
						"goods_name":"商场一楼"
					},
					{
						"goods_id" : "2" ,
						"goods_img" : "../../static/hypermarket/2.png",
						"goods_top":"L2",
						"goods_content":"大食尚 2F05\n 小食神 2F02\n",
						"goods_name":"商场二楼"
					},
					{
						"goods_id" : "3" ,
						"goods_img" : "../../static/hypermarket/3.png",
						"goods_top":"L3",
						"goods_content":"美食点播 3F01\n 食悦轩 4F04\n",
						"goods_name":"商场三楼"
					},
					{
						"goods_id" : "4" ,
						"goods_img" : "../../static/hypermarket/4.png",
						"goods_top":"L4",
						"goods_content":"品味 4F05\n 湘厨 4F03\n",
						"goods_name":"商场四楼"
					},
				]
			}
		},
		onLoad() {
			//this.getRotationList2();
			//this.getGoods();
		},
		methods:{
			navigator(id){
				this.$emit('goodsItemClick',id)
			},
			getRotationList2()
			{
				uni.request({
					url:'http://42.193.114.253:8081/interfaceThreeShow',
						success: (res) => {
						        //console.log(res.data.data);
						        this.rotationList = res.data.data;
							}
				});
			},
			getGoods()
			{
				uni.request({
					url:'http://42.193.114.253:8081/interfaceThreeGoods',
						success: (res) => {
						        console.log(res.data.data);
						        this.goods = res.data.data;
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
	

	.my_title{
	  display: flex;
	  align-items: center;
	  padding: 10rpx;
	  background-color: $main-color;
	}
	
	.logo{
	  flex:7;
	}
	
	.atlas-title{
		color: #222222;
		padding-left: 40rpx;
		padding-bottom: 25rpx;
	}
	
	.hot_goods{
		//background: #eee;
		overflow: hidden;
		margin-top: 10px;
		background-color: #F4F4F4;
	}
	
	.goods_list{
		padding: 0 15rpx;
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		
		.goods_item{
			//background: #fff;
			background-color: $main-color;
			width: 355rpx;
			margin: 10rpx 0;
			padding: 15rpx;
			box-sizing: border-box;
			image{
				width: 80%;
				height: 150px;
				display: block;
				margin: auto;
			}
			.price{
				color: #222222;
				font-size: 36rpx;
				margin: 20rpx 0 5rpx 0;
				text:nth-child(2){
					color: #222222;
					font-size: 28rpx;
					margin-left: 17rpx;
				}
			}
			.name{
				font-size: 28rpx;
				line-height: 50rpx;
				padding-bottom: 15rpx;
				padding-top: 10rpx;
				color: #222222;
			}
		}
	}
	
/* 轮播图 */
.bbs-swiper{
  width: 100%;
  height: 100%;
  border-radius: 15rpx;
}

.bbs-swiper-container{
  width: 90%;
  height: 300rpx;
  margin: 0rpx auto;
  position: relative;
  border-radius: 15rpx;
  overflow: hidden;
}

.bbs-swiper-item{
  width: 100%;
  height: 100%;
  border-radius: 20rpx;
}

.bbs-swiper-item>image{
  width: 100%;
  height: 100%;
  border-radius: 15rpx;
}

.bbs-dots{
  width: auto;
  height: 10rpx;
  position: absolute;
  bottom: 20rpx;
  border-radius: 50rpx;
  left: 270rpx;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 3rpx 10rpx;
}
.bbs-dots-item{
  width: 8rpx;
  height: 8rpx;
  margin: 0rpx 8rpx;
  border-radius: 50%;
  background-color: #cdcdcd;
  transition: all .3s;
}
.bbs-dot-active{
  width: 10rpx;
  height: 10rpx;
  background-color: #fff;
}
</style>
