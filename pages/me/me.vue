<template>
<view class="content">
    <!-- 个人信息 -->
  <view class="top">
    <view class="user-info">
        <view class="user-photo">
            <image src="../../static/anonymous.png"></image>
        </view>
        <!-- 用户名、标签 -->
        <view class="user-tag">
            <view class="user-name">
                <text>所念皆星河</text>
            </view>
            <view class="user-flag">
                <view class="identity">VIP</view>
                <view class="level">Lv10</view>
            </view>
        </view>

        <view class="grow-up">
            <view class="process">
                <image src="../../static/Sign.png" style="opacity: 0.8;"></image>
                <view class="sign">
                    <button size="mini">管理端</button>
                </view>
            </view>
            <view class="grades">
                <view class="exp"></view>
                <view class="exp"></view>
            </view>
        </view>
    </view>

    <!-- 内容分类 -->
    <view class="user-detail">
        <view class="tpye">
            <view class="type-name">就餐订单</view>
            <view class="type-num">2</view>
        </view>
        <view class="tpye">
            <view class="type-name">收藏店铺</view>
            <view class="type-num">24</view>
        </view>
		<view class="tpye">
		    <view class="type-name">足迹</view>
		    <view class="type-num">120</view>
		</view>
		<view class="tpye">
		    <view class="type-name">红包卡券</view>
		    <view class="type-num">12</view>
		</view>
    </view>
  </view>

  <!-- 这里是两个板块 -->
  <view class="middle">
    <view class="middle-content">

        <view class="message">
            <view class="desc-text">
                <view class="title1">您的就餐位置 </view>
                <view class="detail1">小桌 A20</view>
            </view>
            <view class="desc-img1">
               <image src="../../static/message.png"></image>
            </view>
        </view>

        <view class="division">
            <view class="vertical-line">
                <image src="../../static/vertical.png"></image>
            </view>
        </view>

        <view class="about">
            <view class="desc-text">
                <view class="title2">还有 2 桌等待</view>
                <view class="detail2">预计还需 16 分钟</view>
            </view>
            <view class="desc-img2 ">
               <image style="opacity: 0.8;" src="../../static/about.png"></image>
            </view>
        </view>
    </view>
  </view>
      
   <view class="bottom">
     <view class="bottom-content">
         <view class="me-about">
             <text class="title1">您的会员卡</text>
         </view>
         <view class="me-about">
             <text>彭厨</text>
             <image src="../../static/next.png"></image>
         </view>
         <view class="me-about">
             <text>朝花里</text>
             <image src="../../static/next.png"></image>
         </view>
         <view class="me-about">
             <text>湘口福</text>
             <image src="../../static/next.png"></image>
         </view>
         <view class="me-about">
             <text>东北炖肉</text>
             <image src="../../static/next.png"></image>
         </view>
     </view>
   </view>
</view>
</template>


<script>
	export default {
		data() {
			return {
				imageList: [],
			}
		},
		onLoad() {
			//this.imageList = []
		},
		
		methods:{
		   
			
		},
	}
</script>


<style lang="scss">

page {
  background-color: #F4F4F4;
}



.user-info{
  display: flex;
  width: 100%;
  height: 150rpx;
}

.user-photo{
  margin: 20rpx 10rpx 10rpx 20rpx;
  align-self: center;
}
.user-photo image{
  width: 120rpx;
  height: 120rpx;
}


.process image{
  width: 60rpx;
  height: 60rpx;
}

.user-tag{
  display: flex;
  width: 330rpx;
  flex-direction: column;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  z-index: 9999;

}

.user-name{
	display: flex;
	margin: auto;
	margin-left: 0;
	margin-top: 40;
}

.user-name text{
  //color: rgb(244, 243, 241);
  color: #222222;
  font-size: 34rpx;
  font-weight: 800;
}


.user-flag{
  margin: auto;
  margin-left: 0;
  margin-top: 0;
  display: flex;
}
.identity{
  background-color: #C27C88;
  color: gainsboro;
  padding: 5rpx 10rpx;
  font-size: 20rpx;
  border-radius: 8rpx;
}

.level{
  background-color: #3F797A;
  color: white;
  padding: 5rpx 10rpx;
  border-radius: 8rpx;
  margin-left: 10rpx;
  font-size: 20rpx;
}

.grow-up{
  margin-top: 20rpx;
  display: flex;
  flex-direction: column;

  margin-left: 0rpx;
}

.sign{
  display: inline;
}

.process{
  display: flex;
  align-self: center;
}

.grades{

  text-align: center;
  position: relative;
  margin: auto;
  margin-top: 0;
  top: -8rpx;
  font-size: 20rpx;
}

.exp{
  color: $text-color;
  //text-shadow: 2rpx 2rpx 2rpx #726d6d;
  letter-spacing: 1rpx;
}

.user-detail{
  display: flex;
  flex-wrap: wrap;
  margin: auto;
  margin-top: 10rpx;
  padding-top: 10rpx;
  align-items: center;
  justify-content: space-around;
  border-top: 1px solid rgb(214, 203, 203);
}

.type-name{
  //color: rgb(244, 243, 241);
  color: #222222;
  text-align: center;
  font-size: 23rpx;

}

.type-num{
  //color: rgb(244, 243, 241);
  color: #222222;
  text-align: center;
  font-size: 30rpx;
  font-weight: 600;
  position: relative;
  top: -5rpx;
}

.top{
  padding-top: 20rpx;
  //box-shadow: 2rpx 2rpx 2rpx 2rpx $border-color;
  background-color: $me-three-color;
  border-radius: 20rpx;
  //opacity:0.5;
}

/* 中间 */
.desc-img1 image{
  width: 70rpx;
  height: 70rpx;
}

.desc-img2 image{
  width: 100rpx;
  height: 100rpx;
}

.middle{
  display: flex;
  margin-top: 30rpx;
  height: 160rpx;
  //box-shadow: 2rpx 2rpx 5rpx 2rpx $border-color;
  background-color: $me-three-color;
  border-radius: 20rpx;
}

.middle-content{
  height: 120;
  width: 100%;
  padding-left: 20rpx;
  margin: auto;
  align-items: center;
  justify-content: space-around;
  display: flex;
}

.message{
  align-items: center;
  display: flex;
}

.division{
  display: flex;
  align-items: center;
}

.vertical-line image{
  width: 50rpx;
  height: 80rpx;
  z-index: 9999;
  vertical-align: middle;
}

.about{
  align-items: center;
  display: flex;
  image{
	  width: 80rpx;
	  height: 80rpx;
  }
}

.title1{
  font-size: 30rpx;
  font-weight: 800;
  color: $text-color;
}

.detail1{
  font-size: 20rpx;
  font-weight: 500;
  color: $text-color;
}

.title2{
  font-size: 30rpx;
  font-weight: 800;
  color: $text-color;
}

.detail2{
  font-size: 20rpx;
  font-weight: 500;
  color: $text-color;
}


/* 下面 */
.bottom{
  margin-top: 35rpx;
  background-color: $main-color;
}
.bottom-content{
  width: 95%;
  border-radius: 5%;
  margin: auto;
 // background-color: rgb(253, 253, 253);
  padding-bottom: 35rpx;
 // box-shadow: 3rpx 3rpx 5rpx 3rpx $border-color;
  
  background-color: $me-three-color;
}
.me-about{
  display: flex;
  margin: 20rpx 40rpx;
  padding: 30rpx 0rpx;
  justify-content: space-between;
  border-bottom: 2rpx solid white;
  color: #222222;;
}
.me-about image{
  align-self: center;
  width: 35rpx;
  height: 35rpx;
}
</style>
