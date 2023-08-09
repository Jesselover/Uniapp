<template>
	<view>
		<h1>当前页面不存在21111</h1>
		   <myItem></myItem>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		},
		onload(){
			let timer = setTimeout(()=>{
				clearTimeout(timer)
				uni.navigateTo({
					url:'/pages/index/index'
				})
				console.log('欧克、')
			},5000)
		}
	}
</script>

<style>

</style>
