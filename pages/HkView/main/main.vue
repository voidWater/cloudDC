<template >
	<view class="backcol">
		<view class="page-body">
			<view class="page-section page-section-gap">
				<map style="width: 100%; height: 300px;" :latitude="latitude" :longitude="longitude" :markers="covers">
				</map>
			</view>
		</view>
		<view class="input-panel">
			<view class="title">
				惠快同城，海口同城送货最实惠。
			</view>
			
		
			
			<view class="content border2">
				<view>
					<view>地址</view>
					<view>请完善发件信息</view>
				</view>
				<view>
					<u-button shape="circle" size="mini" hair-line="true">地址簿</u-button>
				</view>
			</view>
			
			<view class="content">
				<view>
					<view>地址</view>
					<view>请完善发件信息123</view>
				</view>
				<view>
					<u-button shape="circle" size="mini" hair-line="true">地址簿</u-button>
				</view>
			</view>
		</view>
		
		<view class="gn-list">
			<view class="gn-col">
				<view><u-icon name="red-packet" color="#54B435" size="40"></u-icon></view>
				<view>省钱红包123123</view>
			</view>
			
			<view class="gn-col">
				<view><u-icon name="man-add" color="#54B435" size="40"></u-icon></view>
				<view>成为骑手</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:0, // 使用 marker点击事件 需要填写id
				title: 'map',
				latitude: 39.909,
				longitude: 116.39742,
				covers: [{
					latitude: 39.909,
					longitude: 116.39742,
					iconPath: '../../../static/location.png'
				}, {
					latitude: 39.90,
					longitude: 116.39,
					iconPath: '../../../static/location.png'
				}]
			};
		}
	}
</script>

<style lang="scss">
.input-panel{
	background-color: #fff;
	margin: 20rpx;
	border-radius: 20rpx;
	box-shadow: #fff;
}
.input-panel .title{
	border-radius: 20rpx;
	padding: 20rpx;
	background-color: $uni-color-blue;
	color: #fff;
}
.input-panel .content{
	margin: 40rpx 30rpx;
	padding: 20rpx 30rpx;
	display: flex;
	flex-direction: row;
	justify-content: space-between;
	align-items: center;
}

.border2{
	border:2px solid #54B435;
	border-radius: 25rpx;
}

.gn-list{
	display: flex;
	flex-direction: row;
	justify-content: space-around;
	background-color: #fff;
	margin: 20rpx 20rpx;
	border-radius: 20rpx;
	padding: 25rpx;
	
}
.gn-col{
	display: flex;
	flex-direction: column;
	align-items: center;
}
.backcol{
	background-color: #eaecf2;
}
</style>
