<template>
	<view>
		<h1 class="title">{{title}}</h1>
		<view class="time">
			<uni-icons type="calendar-filled" size=20></uni-icons>
			发表于{{time}}
		</view>
		<view class="article"></view>
	</view>
</template>

<script>
	export default {
		name: "NoteItem",
		data() {
			return {
				title: "杜童菲的笔记",
				time: "2023-7-20"
			};
		}
	}
</script>

<style lang="scss">

</style>