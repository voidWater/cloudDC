<template>
	<view class="container">
		<dc-main v-if="current==0"></dc-main>
		<dc-user v-if="current==2"></dc-user>
		
		<tui-tabbar :isFixed="true" :tabBar="tabBar" hump :current="current" @click="tabbarSwitch"
		></tui-tabbar>
		<!-- <tui-tabbar :current="current" @click="tabbarSwitch"  backdropFilter :backgroundColor="backgroundColor" :tabBar="tabBar" color="#777" selectedColor="#AC9157"></tui-tabbar> -->
	</view>
</template>

<script>
import dcMain from "../componentView/dcMain.vue";
import dcUser from "../componentView/dcUser.vue";
export default {
	components: {dcMain,dcUser},
	data() {
		return {
			current: 0,
			//字体图标
			tabBar: [
				{
					text: '首页',
					name:'shop',
					activeName:'shop-fill',
				},
				{
					text: '点单',
					name:'strategy',
					hump: true,
					activeName:'explore-fill'
				},
				{
					text: '我的',
					name:'people',
					activeName:'people-fill',
					
				}
				// {
				// 	text: '自定义',
				// 	customPrefix:'tui-icon__extend',
				// 	name:'icon-caution',
				// 	activeName:'icon-caution-fill',
				// 	isDot: true
				// }
			],
			backgroundColor: 'rgba(248,248,248,.7)'
		};
	},
	onLoad() {
		// #ifdef H5
		this.backgroundColor = '#f8f8f8';
		// #endif
		// #ifndef H5
		if (this.tui.isAndroid()) {
			this.backgroundColor = '#f8f8f8';
		}
		// #endif
	},
	methods: {
		init(){
			
		},
		tabbarSwitch(e) {
			//获取登录状态，此处默认未登录
			let isLogin = false;
			if (e.verify && !isLogin) {
				this.tui.toast('您还未登录，请先登录');
			} else {
				this.current = e.index;
			}
		}
	}
};
</script>

<style>
/* page {
		background: #EDEDED;
	}
 */
.container {
	padding: 20rpx 0 120rpx 0;
	box-sizing: border-box;
}

.header {
	padding: 80rpx 90rpx 60rpx 90rpx;
	box-sizing: border-box;
}

.title {
	font-size: 34rpx;
	color: #333;
	font-weight: 500;
}

.sub-title {
	font-size: 24rpx;
	color: #7a7a7a;
	padding-top: 18rpx;
}

.tui-mtop {
	margin-top: 80rpx;
}
</style>
