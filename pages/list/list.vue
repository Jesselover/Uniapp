<template>
	<view>
		<!-- navscroll -->
		<scroll-view scroll-x="true" class="navscroll">
			<view class="title">HTML+CSS</view>
			<view class="title">JavaScript</view>
			<view class="title">Vue</view>
			<view class="title">移动端</view>
			<view class="title">workTools</view>
			<view class="title">ThreeJS</view>
		</scroll-view>
		<!-- swiper -->
		<swiper class="swiper" circular :indicator-dots="swiper.indicatorDots" :autoplay="swiper.autoplay"
			:interval="swiper.interval" duration="duration">
			<swiper-item class="swiper-item" v-for=" item in imgs" :key="item.id">
				<image :src="item.src" :alt="item.src" mode="heightFix">
			</swiper-item>
		</swiper>
		<view class="note">
			<NoteItem class="item"></NoteItem>
			<NoteItem class="item"></NoteItem>
			<NoteItem class="item"></NoteItem>
			<NoteItem class="item"></NoteItem>
			<NoteItem class="item"></NoteItem>
			<NoteItem class="item"></NoteItem>
			<NoteItem class="item"></NoteItem>
			<NoteItem class="item"></NoteItem>
			<NoteItem class="item"></NoteItem>
			<NoteItem class="item"></NoteItem>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
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
				swiper: {
					indicatorDots: true,
					autoplay: true,
					interval: 2000,
					duration: 500
				}
			};
		}
	}
</script>

<style lang="scss">
	.navscroll {
		z-index: 1000;
		position: fixed;
		// top:0;
		// left:0;
		padding: 0;
		margin: 0;
		width: 100%;
		white-space: nowrap;
		background-color: #f3d9f6;

		// 去掉自带的滑动条
		// /deep/::-webkit-scrollbar {
		// 	display: none;
		// }

		/deep/::-webkit-scrollbar {
			display: none !important;
			width: 0 !important;
			height: 0 !important;
			-webkit-appearance: none;
			background: transparent;
		}

		.title {
			display: inline-block;
			padding: 20rpx 30rpx;
			background-color: #f3d9f6;
			border-radius: 50rpx;
		}

		.title:hover {
			background-color: #c7a4c4;
		}
	}
	.swiper {
		width: 100%;
		height: 500rpx;
		padding-top: 66rpx;
		.swiper-item {
			display: block;
			line-height: 300rpx;
			text-align: center;
	
			image {
				width: 100%;
				height: 500rpx;
			}
		}
	}
	.note {
		padding-top: 20rpx;
		.item {
			width: 100%;
			height: 250rpx;
			margin-bottom: 10rpx;
			background-color: $pink-one;
		}
	}
</style>