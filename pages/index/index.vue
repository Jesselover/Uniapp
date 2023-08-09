<template>
	<view class="content">
		<!-- image标签默认宽高为320/240 -->
		<!-- scroll-view  -->
		<scroll-view scroll-x class="scroll">
			<view class="group">
				<view class="item" v-for=" item in imgs" :key="item.id">
					<image :src="item.src" :alt="item.src">
				</view>
			</view>
		</scroll-view>
		<view>
			<h1 class="title">{{title}}</h1>
			<navigator url="/pages/404/404" class="text-area" >404</navigator>
			<navigator url="/pages/list/list" open-type="reLaunch" class="text-area">list/relaunch</navigator>
			<navigator url="/pages/list/list" class="text-area">list</navigator>
			<navigator url="/pages/login/login" class="text-area">登录</navigator>
			<navigator url="/pages/register/register" class="text-area">注册</navigator>
			<!-- ? echart的引入 -->
			<navigator url="/pages/Echarts/Echarts" class="text-area">echarts</navigator>
		</view>


	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: '杜童菲的uniapp学习',
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
		methods: {

		},
		onLoad() {}
	}
</script>

<style lang='scss'>
	/* rpx把所有设备的屏幕，在宽度上等分为750份(即：当前屏幕的总宽度为750rpx)。 */

	image {
		height: 400rpx;
		width: 400rpx;
	}

	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;

		.title {
			font-size: 36rpx;
			color: #d46f7f;
		}
	}

	.logo {
		margin: 200rpx auto 50rpx auto;
	}

	.text-area {
		display: flex;
		justify-content: center;
		white-space: nowrap;
	}

	.scroll {
		height: 400rpx;
		width: 200px;
		margin: 100rpx auto 50rpx auto;
		padding: 5rpx;
		border: 15rpx solid #d9aaa6;
		border-radius: 20rpx;

		.group {
			white-space: nowrap;

			.item {
				display: inline-block
			}
		}
	}

</style>