<template>
	<view>
		<heardNavbar iconColor="#606266"></heardNavbar>
		<view class="content">
			<view class="title">
				蜂鸟外卖
			</view>
			<view class="login">
				<view class="tabs">
					<u-tabs :list="tabs" @click="checkout" lineWidth="120rpx">
					</u-tabs>
				</view>
				<view class="form">
					<u--form labelPosition="left" :model="form" :rules="rules" ref="form1">
						<u-form-item prop="phone" ref="item1">
							<!-- #ifndef APP-NVUE -->
							<u-input placeholder="请输入手机号" v-model="form.phone">
								<!-- #endif -->
								<!-- #ifdef APP-NVUE -->
								<u--input placeholder="请输入手机号" v-model="form.phone">
									<!-- #endif -->
									<template slot="suffix">
										<u-code ref="uCode" @change="codeChange" seconds="60" changeText="x秒重新获取">
										</u-code>
										<u-button @tap="getCode" :text="tips" type="success" size="mini"></u-button>
									</template>
									<!-- #ifndef APP-NVUE -->
							</u-input>
							<!-- #endif -->
							<!-- #ifdef APP-NVUE -->
							</u--input>
							<!-- #endif -->

						</u-form-item>
						<u-form-item prop="phone" ref="item1">
							<u--input placeholder="验证码" border="surround" v-model="form.code" @change="change">
							</u--input>
						</u-form-item>
					</u--form>

					<view class="text">
						温馨提示:未注册蜂鸟外卖帐号的手机号，登录时将自动注册，且代表已同意<text style="color:'#02a774'">《用户服务协议》</text>
					</view>
				</view>

				<view class="form">
					<u--input placeholder="请输入手机号" border="surround" v-model="form.phone" @change="change"></u--input>
					<u--input placeholder="请输入密码" border="surround" v-model="form.code" @change="change"></u--input>
					<u--input placeholder="验证码" border="surround" v-model="form.code" @change="change"></u--input>
				</view>


			</view>
			<view class="bottom">
				<view class="button">
					登录
				</view>
				<view class="about">
					关于我们
				</view>
			</view>

		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tabs: [{
					name: '短信登录'
				}, {
					name: '密码登录'
				}],
				form: {
					phone: '',
					code: ''
				},
				tips: '',
				rules: {
					phone: {
						type: 'string',
						required: true,
						message: '请输入手机号',
						trigger: ['blur', 'change']
					}
				}
			}
		},
		methods: {
			checkout(i) {
				console.log(i)
			},

			codeChange(text) {
				this.tips = text;
			},
			getCode() {
				if (this.$refs.uCode.canGetCode) {
					// 模拟向后端请求验证码
					uni.showLoading({
						title: '正在获取验证码'
					})
					setTimeout(() => {
						uni.hideLoading();
						// 这里此提示会被this.start()方法中的提示覆盖
						uni.$u.toast('验证码已发送');
						// 通知验证码组件内部开始倒计时
						this.$refs.uCode.start();
					}, 2000);
				} else {
					uni.$u.toast('倒计时结束后再发送');
				}
			},
			change(e) {
				console.log('change', e);
			}

		}
	}
</script>

<style lang="scss">
	.header-nav {
		background-color: white;
	}

	.content {
		padding: 70rpx;

		.title {
			font-size: 68rpx;
			font-weight: 600;
			color: #02a774;
			text-align: center;
			margin-bottom: 76rpx;
		}



		.login {
			.tabs {
				display: flex;
				justify-content: center;
				margin-bottom: 20rpx;
			}

			.form {
				position: relative;

				.u-input {
					// margin-bottom: 40rpx;
					height: 70rpx;
				}

				.get-code {
					width: 140rpx;
					height: 100rpx;
					line-height: 100rpx;
					position: absolute;
					color: #ccc;
					font-size: 28rpx;
					right: 10rpx;
					top: 0rpx;
				}

				.text {
					font-size: 28rpx;
					color: #999;
				}
			}
		}

		.bottom {
			margin-top: 60rpx;

			.button {
				width: 100%;
				height: 84rpx;
				text-align: center;
				line-height: 84rpx;
				background-color: #4cd96f;
				color: #fff;
				font-size: 36rpx;
				border-radius: 6px;
			}

			.about {
				font-size: 30rpx;
				text-align: center;
				color: #999;
				margin-top: 30rpx;
			}
		}
	}
</style>
