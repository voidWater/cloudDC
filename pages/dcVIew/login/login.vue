<template>
	<view style="text-align: center;padding-top: 200rpx;">
		<view>豆腐干豆腐干</view>
		<view class="tui-group-box">
			<tui-image-group :imageList="imageList" width="150rpx" height="150rpx"></tui-image-group>
		</view>
		<view style="margin-top: 25rpx;margin-bottom: 50rpx;">
			{{storeName}}
		</view>
		<view style="margin: 100rpx 60rpx 60rpx 60rpx;text-align: left;">
			<view style="font-size: 30rpx;margin-bottom: 25rpx;">该小程序将获取以下授权：</view>
			<view style="font-size: 25rpx;color: #eaeaea">获取您公开的信息（昵称、头像等）</view>
		</view>
		<view style="margin: 30rpx;">
			<tui-button style="background-color: #5a6962;"
			margin="0 20rpx 26rpx 0;" height="85rpx" :size="32"
			color="#5a6962" shape="circle" :disabled="but" @click="detail">微信授权登录/注册</tui-button>
		</view>
		<view style="margin: 50rpx 30rpx;font-size: 25rpx;display: flex;flex-direction: row;justify-content: start;align-items: center;">
			<radio-group @change="radioChange" style="transform: scale(0.77)">
				<label class="radio"><radio :color="color"  value="r1" checked="true" /></label>
			</radio-group>
		
			我已阅读并同意
			<text>《用户服务协议》</text>和
			<text>《用户隐私协议》</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name:"慢板咖啡",
				imageList:[{
					id:1,
					src:"/static/images/product/2.jpg"
				}],
				but:true,
				storeName:"",
				color:""
			};
		},
		onLoad() {
			this.storeName = this.$store.state.storeName
			this.color = this.$store.state.color
			console.log(this.color)
		},
		reback(){
			
		}
	}
</script>

<style lang="scss">
.sa{
	color: #5a6962;
}
</style>

