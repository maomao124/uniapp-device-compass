<template>
	<view>
		<h2>direction:{{direction}}</h2>
		<button type="primary" @click="button1">监听罗盘数据</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				direction:0,
			}
		},
		methods: {
			button1()
			{
				const f = function(res)
				{
					console.log(res.direction);
					this.direction = res.direction;
				}
				console.log("监听罗盘数据");
				uni.onCompassChange(f);
			}
		}
	}
</script>

<style>

</style>
