<template>
	<view>
		<h2>direction:{{direction}}</h2>
		<button type="primary" @click="button1">注册监听罗盘数据回调</button>
		<button type="primary" @click="button2">取消注册监听罗盘数据回调</button>
		<button type="primary" @click="button3">开始监听罗盘数据</button>
		<button type="primary" @click="button4">停止监听罗盘数据</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				direction: 0,
				f:undefined
			}
		},
		methods: {
			button1()
			{
				if(!this.f)
				{
					this.f = (res)=>
					{
						console.log(res.direction);
						this.direction = res.direction;
					}
					console.log("监听罗盘数据");
					uni.onCompassChange(this.f);
				}
			},
			button2()
			{
				if(this.f)
				{
					console.log("取消监听罗盘数据");
					uni.offCompassChange(this.f);
					this.f = undefined;
				}
			},
			button3()
			{
				uni.startCompass({
					success: () => {
						uni.showToast({
							title:'成功'
						})
					},
					fail: () => {
						uni.showToast({
							title:'失败'
						})
					}
				})
			},
			button4()
			{
				uni.stopCompass({
					success: () => {
						uni.showToast({
							title:'成功'
						})
					},
					fail: () => {
						uni.showToast({
							title:'失败'
						})
					}
				})
			}
		}
	}
</script>

<style>
button{
	margin: 5px;
}
</style>
