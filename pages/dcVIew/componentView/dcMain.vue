<template>
  <div>
	  <image style="width: 100%;height: 400rpx" src="https://market-to-home.oss-accelerate.aliyuncs.com/image/20231108121822243-7632-1.png"></image>
	  <view class='tui-notice-board'>
	  	<view class="tui-icon-bg">
	  		<tui-icon name="news-fill" :size='24' color='#f54f46'></tui-icon>
	  	</view>
	  	<view class="tui-scorll-view" >
	  		<view class="tui-notice" :class="[animation?'tui-animation':'']">B站10分日本动漫已消失，9.9分仅剩12部，这一部动漫包揽三席！</view>
	  	</view>
	  </view>
	  <view class="panel">
	  	<view class="ssd">
	  		<view>
	  			<view>
	  				欢迎光临{{storeName}}
	  			</view>
	  			<view class="small">
	  				登录成为会员，享更多权益
	  			</view>
	  		</view>
	  		<tui-button margin="0 20rpx 26rpx 0" type="green" shape="circle" width="150rpx" height="60rpx" :size="24" @click="detail">立即登录</tui-button>
	  	</view>
	  </view>
  </div>
</template>

<script>
export default {
  name: "",
  data() {
    return {};
  },
  props: {
    content: "",//接收参数
  },
  components: {},
  created() {},
  mounted() {},
  methods: {},
};
</script>
<style lang="scss" scoped>
.title-small {
    background-color: rgb(231, 231, 231);
    padding: 8px 16px;
    width: 500px;
    border-radius: 2px;
  .icon {
    width: 16px;
    height: 16px;
    border-radius: 8px;
    border: 2px solid rgb(19, 180, 230);
  }
  .text {
    font-size: 16px;
  }
}


.tui-notice-board {
	width: 100%;
	padding-right: 30rpx;
	box-sizing: border-box;
	font-size: 28rpx;
	height: 60rpx;
	background: #fff8d5;
	display: flex;
	align-items: center;
	position: fixed;
	top: 0;
	/* #ifdef H5 */
	top: 44px;
	/* #endif */
	z-index: 999;
}

.tui-icon-bg {
	background: #fff8d5;
	padding-left: 30rpx;
	position: relative;
	z-index: 10;
}

.tui-icon-class {
	margin-right: 12rpx;
}

.tui-scorll-view {
	flex: 1;
	line-height: 1;
	white-space: nowrap;
	overflow: hidden;
	color: #f54f46;
}

.tui-notice {
	-webkit-backface-visibility: hidden;
	-webkit-perspective: 1000;
	transform: translate3d(100%, 0, 0);
}

.tui-animation {
	-webkit-animation: tui-rolling 12s linear infinite;
	animation: tui-rolling 12s linear infinite;
}

@-webkit-keyframes tui-rolling {
	0% {
		transform: translate3d(100%, 0, 0);
	}

	100% {
		transform: translate3d(-170%, 0, 0);
	}
}

@keyframes tui-rolling {
	0% {
		transform: translate3d(100%, 0, 0);
	}

	100% {
		transform: translate3d(-170%, 0, 0);
	}
}

.tui-subject {
	padding: 100rpx 30rpx 30rpx 30rpx;
	box-sizing: border-box;
	font-size: 32rpx;
	font-weight: bold;
}

.tui-rolling-news {
	width: 100%;
	padding: 12rpx 30rpx;
	box-sizing: border-box;
	display: flex;
	align-items: center;
	justify-content: center;
	flex-wrap: nowrap;
}

.tui-swiper {
	font-size: 28rpx;
	height: 50rpx;
	flex: 1;
}

.tui-swiper-item {
	display: flex;
	align-items: center
}

.tui-news-item {
	line-height: 28rpx;
	white-space: nowrap;
	overflow: hidden;
	text-overflow: ellipsis;
}

.tui-searchbox {
	padding: 60rpx 80rpx;
	box-sizing: border-box;
}

.tui-rolling-search {
	width: 100%;
	height: 70rpx;
	border-radius: 35rpx;
	padding: 0 40rpx 0 30rpx;
	box-sizing: border-box;
	background: #fff;
	display: flex;
	align-items: center;
	justify-content: center;
	flex-wrap: nowrap;
	color: #999;
}
</style>

