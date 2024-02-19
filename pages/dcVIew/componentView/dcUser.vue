<template>
	<view>
		<tui-navigation-bar splitLine @init="initNavigation" @change="opacityChange"  title="NavBar自定义导航栏" backgroundColor="#fff" color="#333">
			<!-- #ifndef MP-ALIPAY || MP-BAIDU -->
			<view class="tui-header-icon" :style="{ marginTop: top + 'px' }"><tui-icon name="arrowleft" :color="opacity > 0.85 ? '#333' : '#fff'" @click="back"></tui-icon></view>
			<!-- #endif -->
		</tui-navigation-bar>
		<!--1-->
		<view class="head">
			<tui-icon name="imface" size="35" color="#999"></tui-icon>
			<tui-button margin="0 20rpx 26rpx 0" type="green" shape="circle" width="150rpx" height="60rpx" :size="24" @click="detail">登录/注册</tui-button>
		</view>
		<!--2-->
		
		<view class="panel">
			<image style="width: 100%;height: 400rpx" src="https://market-to-home.oss-accelerate.aliyuncs.com/image/20231108121822243-7632-1.png"></image>
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
		<!--3-->
		<view class="server">
			<view style="margin: 30rpx 50rpx 50rpx 20rpx; ">我的服务</view>
			<tui-grid>
				<block v-for="(item,index) in dataList" :key="index">
					<tui-grid-item :cell="4" @click="detail">
						<view class="tui-grid-icon">
							<tui-icon :name="item.name" :size="item.size" :color="item.color"></tui-icon>
						</view>
						<text class="tui-grid-label">{{item.name}}</text>
					</tui-grid-item>
				</block>
			</tui-grid>
		</view>
		
		<view class="server">
			<view class="server">店铺管理</view>
			<view v-for="(item,index) in glList" :key="index">
				{{item.name}}
			</view>
			<!-- <tui-grid>
				<block v-for="(item,index) in glList" :key="index">
					<tui-grid-item :cell="4"  @click="detail">
						<view class="tui-grid-icon">
							<tui-icon :name="item.name" :size="item.size" :color="item.color"></tui-icon>
						</view>
						<text class="tui-grid-label">{{item.name}}</text>
					</tui-grid-item>
				</block>
			</tui-grid> -->
		</view>
		
		<view style="padding: 20px;">
				<u-button type="primary" text="确定"></u-button>
				<u-button type="primary" :plain="true" text="镂空"></u-button>
				<u-button type="primary" :plain="true" :hairline="true" text="细边"></u-button>
				<u-button type="primary" :disabled="disabled" text="禁用"></u-button>
				<u-button type="primary" loading loadingText="加载中"></u-button>
				<u-button type="primary" icon="map" text="图标按钮"></u-button>
				<u-button type="primary" shape="circle" text="按钮形状"></u-button>
				<u-button text="渐变色按钮" color="linear-gradient(to right, rgb(66, 83, 216), rgb(213, 51, 186))"></u-button>
				<u-button type="primary" size="small" text="大小尺寸"></u-button>
			</view>
		
		<!--4-->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				dataList:[{
					name: "refresh",
					size: 50
				}, {
					name: "search",
					size: 50
				}, {
					name: "ios",
					size: 50
				}, {
					name: "android",
					size: 50
				}],
				glList:[{
					name: "refresh",
					text:"商品管理",
					size: 45
				}, {
					name: "search",
					text:"会员管理",
					size: 45
				}, {
					name: "ios",
					text:"订单管理",
					size: 45
				}, {
					name: "android",
					text: "营销管理",
					size: 45
				}],
				storeName:""
			};
		},
		onLoad() {
			this.storeName = this.$store.state.setting.storeName
			console.log(this.$store.state.setting)
		},
		methods: {
			initNavigation(e) {
				this.opacity = e.opacity;
				this.top = e.top;
			},
			opacityChange(e) {
				this.opacity = e.opacity;
			},
			back() {
				uni.navigateBack();
			}
		},
		onPageScroll(e) {
			this.scrollTop = e.scrollTop;
		}
	}
</script>

<style lang="scss">
.head{
	display: flex;
	flex-direction: row;
	justify-content: start;
	align-items: center;
	padding: 25rpx 20rpx;
	background-color: #fff;
}
.panel{
	margin: 20rpx;
	font-size: 35rpx;
	background-color: #fff;
	border-radius: 20rpx;
}
.panel image{
	border-radius: 20rpx 20rpx 0 0;
}
.panel .ssd{
	padding: 20rpx;
	display: flex;
	flex-direction: row;
	justify-content: space-between;
	align-items: center;
}
.panel .small{
	font-size: 22rpx;
	color: #afafaf;
}
.panel .but{
	background-color: #5a6962;
}
.server{
	margin: 20rpx;
	background-color: #fff;
}
.tui-grid-icon {
		width: 90rpx;
		height: 90rpx;
		margin: 0 auto;
		text-align: center;
		vertical-align: middle;
	}
.tui-grid-label {
		display: block;
		text-align: center;
		font-weight: 400;
		color: #333;
		font-size: 28rpx;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
		margin-top: 10rpx;
	}
</style>
