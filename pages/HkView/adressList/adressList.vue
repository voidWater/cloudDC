<template>
	<view>
		<view v-if="addressList.length < 1" style="margin-top:30rpx">
			<u-empty
			        mode="history" text="无地址记录"
			>
			</u-empty>
		</view>
		<view>
		      <u-swipe-action>
		        <u-swipe-action-item v-for="item of addressList" :options="options1">
		          <view class="swipe-action u-border-top u-border-bottom">
		            <view class="swipe-action__content">
						<view><text class="swipe-action__content__text">{{item.receiverAddress}}</text></view>
						<view>
							<text>item.</text>
						</view>
		            </view>
		          </view>
		        </u-swipe-action-item>
		      </u-swipe-action>
		</view>
	</view>
	
</template>

<script>
	import {
		mapState
	} from 'vuex';
	export default {
		computed: mapState(['ssoUser']),
		data() {
			return {
				options1: [{
							text: '删除'
						}],
				addressList:[]
			};
		},
		onLoad() {
			console.log(this.ssoUser)
			if(this.ssoUser){
				this.tui.request("/app/dc/deliveryAddress/page","GET",{token:this.ssoUser.token},true,false,true).then(res=>{
					console.log(res)
					if(res.code==0){
						this.addressList = res.data.records
					}
					
				})
			}else{
				this.tui.toast("请先登录！")
			}
		}
	}
</script>

<style lang="scss">

</style>
