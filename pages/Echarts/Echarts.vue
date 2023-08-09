<template>
	<view>
		<echarts :option="option" >echarts</echarts>
	</view>
</template>

<script>
	import echarts from '@/components/echarts/echarts.vue';
	export default {
		components: {
			echarts
		},
		data() {
			return {
				option: {
					xAxis: {
						type: 'category',
						data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
					},
					yAxis: {
						type: 'value'
					},
					series: [{
						data: [150, 230, 224, 218, 135, 147, 260],
						type: 'line'
					}]
				}
			}
		},
		methods: {

		}
	}
</script>

<style>

</style>