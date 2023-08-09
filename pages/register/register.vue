<template>
	<view>
		<view class="form">
			<form @submit="formSubmit" @reset="formReset">
				<view class="row">
					<view class="title">姓名</view>
					<input class="uni-input" name="nickname" placeholder="请输入姓名" maxlength="6" />
				</view>
				<view class="row">
					<view class="title">性别</view>
					<radio-group name="gender">
						<label>
							<radio value="男" /><text>男</text>
						</label>
						<label>
							<radio value="女" /><text>女</text>
						</label>
					</radio-group>
				</view>
				<view class="row">
					<view class="title">邮箱</view>
					<input class="uni-input" name="email" placeholder="请输入邮箱" />
				</view>
				<view class="row">
					<view class="title">爱好</view>
					<checkbox-group name="hobby">
						<label>
							<checkbox value="读书" /><text>读书</text>
						</label>
						<label>
							<checkbox value="写字" /><text>写字</text>
						</label>
						<label>
							<checkbox value="其他" /><text>其他</text>
						</label>
					</checkbox-group>
				</view>
				<view class="row">
					<view class="title">年龄</view>
					<slider value="20" name="age" show-value></slider>
				</view>
				<view class="row">
					<view class="title" style="display:inline-block">学历</view>
					<picker style="display:inline-block; width:80%;text-align: center;" :range="options" name="degree"
						:value="selectValue">
						<view>{{options[selectValue]}}</view>
					</picker>
					<!-- value 是索引值，name、degree传的也是索引值，要传其他值，则需要修改 -->
				</view>
				<view class="row">
					<view class="title">密码</view>
					<input class="uni-input" name="psw" placeholder="请输入密码" password maxlength="16" />
				</view>
				<view class="row">
					<view class="title">确认密码</view>
					<input class="uni-input" name="psw2" placeholder="请再次输出密码" password maxlength="16" />
				</view>
				<view class="row agree">
					<view class="title">我同意被收集以上信息</view>
					<view>
						<switch name="agree" color="hotpink" style="transform:scale(0.7)" />
					</view>
				</view>
				<view class="btns">
					<button form-type="submit" hover-class="hover_btn">登录</button>
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
				options: ["高中", "大专", "本科", "研究生", "博士"],
				selectValue: 2,
				formData: {},
				rule: [{
						name: "nickname",
						checkType: 'notnull',
						checkRule: " ",
						errorMsg: "姓名不能为空"
					},
					{
						name: "gender",
						checkType: "in",
						checkRule: "男,女",
						errorMsg: "请选择性别"
					},
					{
						name: "email",
						checkType: "email",
						checkRule: "",
						errorMsg: "邮箱格式错误"
					},
					{
						name: "hobby",
						checkType: "notnull",
						checkRule: "",
						errorMsg: "请至少选择一项爱好"
					},
					{
						name: "psw",
						checkType: "string",
						checkRule: "6,16",
						errorMsg: "请输入6~16位密码"
					},
					{
						name: "agree",
						checkType: "same",
						checkRule: true,
						errorMsg: "请同意被收集以上信息"
					},

				]
			}
		},
		methods: {
			formSubmit: function(e) {
				this.formData = e.detail.value
				const checkRes = graceChecker.check(this.formData, this.rule)
				console.log('form发生了submit事件，携带数据为：' + JSON.stringify(e.detail.value))
				const pswCheck = this.formData.psw.trim() === this.formData.psw2.trim() ? true : false
				if (checkRes && pswCheck) {
					uni.showToast({
						title: "验证通过!",
						icon: "none"
					});
					this.submit()
				} else if (!pswCheck) {
					uni.showToast({
						title: "密码不一致",
						icon: "none"
					});
				} else {
					uni.showToast({
						title: graceChecker.error,
						icon: "none"
					});
				}

			},
			formReset: function(e) {
				console.log('清空数据')
			},
			submit(){
				// 将信息提交给后端
				uni.navigateTo({
					url:`/pages/login/login?email=${this.formData.email}&psw=${this.formData.psw}`
				})
			},
		}
	}
</script>

<style>
	button {
		margin: 30rpx auto;
		background-color: lightpink;
		color: white;
		font-weight: 700;
	}

	label {
		margin: 0 15rpx
	}

	.form {
		width: 600rpx;
		margin: 50rpx auto;
		padding: 25rpx 15rpx;
		border: 15rpx solid hotpink;
		border-radius: 20rpx;
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
</style>