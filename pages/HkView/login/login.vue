<template>
	<view class="container">
		<view class="tui-bg-box">
			<image src="/static/images/login/bg_login.png" class="tui-bg-img"></image>
			<image src="/static/images/my/mine_def_touxiang_3x.png" class="tui-photo"></image>
			<view class="tui-login-name">请登录</view>
		</view>
		<form :report-submit="true" @submit="formLogin">
			<view class="tui-login-from">
				<!-- <view class="tui-line-cell">
					<tui-icon name="mobile" :size="20" color="#6d7a87"></tui-icon>
					<input placeholder-class="tui-phcolor" class="tui-input" name="mobile" placeholder="请输入手机号码"
						maxlength="11" v-model="mobile" type="number" />
				</view>
				<view class="tui-line-cell tui-top28">
					<tui-icon name="pwd" :size="20" color="#6d7a87"></tui-icon>
					<input placeholder-class="tui-phcolor" class="tui-input" name="smsCode" placeholder="请输入验证码"
						maxlength="6" />
					<tui-button width="182rpx" height="56rpx" :size="24" :type="type" shape="circle" :plain="true"
						:disabled="disabled" @click="btnSend">{{ btnText }}</tui-button>
				</view> -->
				<button class="tui-button-primary tui-btn-submit" hover-class="tui-button-hover"
					form-type="submit" open-type="getPhoneNumber" @getphonenumber="getPhoneNumber">登录</button>
				<view class="tui-protocol" hover-class="opcity" :hover-stay-time="150">
					点击"登录"即表示已同意
					<text class="tui-protocol-red" @tap="protocol">《用户协议》</text>
				</view>
			</view>
		</form>
		
		<!-- <view style="margin: 50rpx;">
			<view>
				<viwe>惠快同城</viwe>
				<viwe>全城配送</viwe>
			</view>
			<view>
				<u-button type="success" @click="login">手机号快速验证</u-button>
				<button open-type="getPhoneNumber" @getphonenumber="getPhoneNumber">唤起授权手机号</button>
			</view>
			<view>
				
			</view>
			<view>
				<u-button type="success">暂不登录</u-button>
			</view>
		</view> -->
	</view>
	
</template>

<script>
import tui from '../../../common/httpRequest';
	export default {
		data() {
			return {
				
			};
		},
		methods:{
			getPhoneNumber(e){
				uni.login({
				  provider: 'weixin',
				  success:res=>{
					  if(res.code){
						  this.tui.request("/common/sso/code2Session","GET",{code:res.code},true,false,true).then(res=>{
							if(res.code=="0"){
								this.tui.request("/common/sso/login","GET",{
									type: 3,
									deviceType: 0,
									target: 1,
									keepLoggedFlag: 1,
									wechatEncryptedData: e.detail.encryptedData,
									wechatIv: e.detail.iv,
									wechatSessionKey: res.data.sessionKey,
									wechatOpenId: res.data.openId,
									wechatUnionId: res.data.unionId
								},true,false,true).then(res=>{
									console.log(res)
									if(res.code=='0'){
										if(res.data && res.data.ssoUser && res.data.token){
											this.tui.toast('登录成功');
											res.data.ssoUser.token = res.data.token;
											this.$store.commit('login', res.data.ssoUser);
												uni.switchTab({
													url: '/pages/HkView/user/user',fail(e){
													console.log(e)
												}
											});
										}else{
											this.tui.toast('登录失败，请重试~');
										}
									}else{
										this.tui.toast('登录失败，请重试~');
									}					 
								})
							}			 
						  })
					  }
					 
				  }
				});
			},
			login:function(){
				this.tui.toast('全部文章');
				/**
				 * 请求数据处理
				 * @param string url 请求地址
				 * @param string method 请求方式
				 *  GET or POST
				 * @param {*} postData 请求参数
				 * @param bool isDelay 是否延迟显示loading
				 * @param bool isForm 数据格式
				 *  true: 'application/x-www-form-urlencoded'
				 *  false:'application/json'
				 * @param bool hideLoading 是否隐藏loading
				 *  true: 隐藏
				 *  false:显示
				 */
				//
				uni.login({
				  provider: 'weixin',
				  success:res=>{
					  console.log(res)
					 this.tui.request("/common/sso/code2Session","GET",{code:res.code},true,false,true).then(res=>{
						console.log(res)
						if(res.code=='0'){
							this.tui.toast('登录成功');
							this.$store.commit('login', res.data.ssoUser,res.data.token);
							console.log();
						}else{
							this.tui.toast('注册失败，请重试~');
						}
					 })
				  }
				});
			},
			protocol: function() {
				uni.navigateTo({
					url: '/pages/doc/protocol/protocol'
				});
			}
		}
		
	}
</script>

<style lang="scss">
page {
		background-color: #fff;
	}

	.tui-bg-box {
		width: 100%;
		box-sizing: border-box;
		position: relative;
		padding-top: 44rpx;
	}

	.tui-photo {
		height: 138rpx;
		width: 138rpx;
		display: block;
		margin: 10rpx auto 0 auto;
		border-radius: 50%;
		position: relative;
		z-index: 2;
	}

	.tui-login-name {
		width: 128rpx;
		height: 40rpx;
		font-size: 30rpx;
		color: #fff;
		margin: 36rpx auto 0 auto;
		text-align: center;
		position: relative;
		z-index: 2;
	}

	.tui-bg-img {
		width: 100%;
		height: 346rpx;
		display: block;
		position: absolute;
		top: 0;
	}

	.tui-login-from {
		width: 100%;
		padding: 128rpx 104rpx 0 104rpx;
		box-sizing: border-box;
	}

	.tui-input {
		font-size: 32rpx;
		flex: 1;
		display: inline-block;
		padding-left: 32rpx;
		box-sizing: border-box;
		overflow: hidden;
	}

	.tui-line-cell {
		padding: 27rpx 0;
		display: -webkit-flex;
		display: flex;
		-webkiit-align-items: center;
		align-items: center;
		position: relative;
		box-sizing: border-box;
		overflow: hidden;
	}

	.tui-line-cell::after {
		content: '';
		position: absolute;
		border-bottom: 1rpx solid #e0e0e0;
		-webkit-transform: scaleY(0.5);
		transform: scaleY(0.5);
		bottom: 0;
		right: 0;
		left: 0;
	}

	.tui-top28 {
		margin-top: 28rpx;
	}

	.tui-btn-class {
		width: 196rpx !important;
		height: 54rpx !important;
		border-radius: 27rpx !important;
		font-size: 28rpx !important;
		padding: 0 !important;
		line-height: 54rpx !important;
	}

	.tui-btn-submit {
		margin-top: 100rpx;
	}

	.tui-protocol {
		color: #333;
		font-size: 24rpx;
		text-align: center;
		width: 100%;
		margin-top: 29rpx;
	}

	.tui-protocol-red {
		color: #f54f46;
	}
</style>
