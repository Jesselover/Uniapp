<template>
	<view>
		<!-- scroll-view  -->
		<scroll-view scroll-x class="scroll">
			<view class="group">
				<view class="item" v-for=" item in imgs" :key="item.id">
					<image :src="item.src" :alt="item.src">
				</view>
			</view>
		</scroll-view>
		<view class="form box">
			<form @submit="formSubmit" @reset="formReset">

				<view class="row">
					<view class="title">邮箱</view>
					<input class="uni-input" name="email" placeholder="请输入邮箱" :value="formData.email" />
				</view>

				<view class="row">
					<view class="title">密码</view>
					<input class="uni-input" name="psw" placeholder="请输入密码" password maxlength="16"
						:value="formData.psw" />
				</view>
				<view class="btns">
					<button form-type="submit">登录</button>
					<button form-type="reset">重置</button>
				</view>
			</form>
		</view>
	</view>
</template>
<script>
	import graceChecker from "../../common/graceChecker.js"
	export default {
		data() {
			return {
				formData: {},
				rule: [{
						name: "email",
						checkType: "email",
						checkRule: "",
						errorMsg: "邮箱格式错误"
					},
					{
						name: "psw",
						checkType: "string",
						checkRule: "6,16",
						errorMsg: "请输入6~16位密码"
					},
				],
				imgs: [{
						id: 2,
						src: '/static/2.jpg'
					},
					{
						id: 3,
						src: '/static/3.jpg'
					}, {
						id: 4,
						src: '/static/4.jpg',
					}, {
						id: 5,
						src: '/static/5.jpg'
					}, {
						id: 6,
						src: '/static/6.jpg',
					},
				],
			}
		},
		onLoad(e) {
			this.formData = {
				email: e.email,
				psw: e.psw
			}
			console.log(this.formData);
			this.formReset()
		},
		methods: {
			formSubmit: function(e) {

				this.formData = e.detail.value
				const checkRes = graceChecker.check(this.formData, this.rule)
				if (checkRes) {
					uni.showToast({
						title: "验证通过!",
						icon: "none"
					});
					this.submit()
				} else {
					uni.showToast({
						title: graceChecker.error,
						icon: "none"
					});
				}

			},
			formReset: function(e) {
				console.log('清空数据')
				this.formData = {}
			},
			submit() {
				uni.showLoading({
					title: '加载中'
				});
				setTimeout(function () {
					uni.hideLoading();
					// 登录接口
					uni.navigateTo({
						url: "/pages/list/list",
					})
				}, 1000);
			
			},
		}
	}
</script>

<style lang="scss">

	.scroll {
		height: 400rpx;
		width: 200px;
		margin: 100rpx auto 50rpx auto;
		padding: 5rpx;
		border: 15rpx solid $purple-three;
		border-radius: 20rpx;

		.group {
			white-space: nowrap;

			.item {
				display: inline-block
			}
		}

		image {
			height: 400rpx;
			width: 400rpx;
		}
	}

	.box {
		width: 600rpx;
		margin: 50rpx auto;
		padding: 25rpx 15rpx;
	}

	.form {
		// border: 15rpx solid deeppink;
		border-radius: 20rpx;

		button {
			margin: 30rpx auto;
			background-color: $purple-three;
			color: white;
			font-weight: 700;
		}
		
		button:hover{
			background-color: $purple-four;
		}
		
		label {
			margin: 0 15rpx
		}

		.row {
			padding: 15rpx;
		}

		.agree {
			font-size: 14rpx;
			text-align: center;
		}

		.title {
			padding: 15rpx 0;
		}

		.btns {
			width: 600rpx
		}

		.hover_btn {
			background-color: deeppink;
		}
	}
</style>