<template>
	<view>
		<view class="u-flex u-p-20">
			<u-image class='u-m-r-30' width="150rpx" height="150rpx" src="/static/icon/icon6.png"></u-image>
			<view class="u-font-30">
				新疆小苹果 1.5KG
			</view>
		</view>
		<u-gap height="20" bg-color="#f5f5f5">这个商品很不错</u-gap>
		<view v-for="(item,index) in 10" :key="index">
			<evaluate-item class="u-p-l-20 u-p-r-20"></evaluate-item>
			<u-gap height="20" bg-color="#f5f5f5"></u-gap>
		</view>
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
		onLoad(param) {
			console.log(param)
			let a = param.arrItem.toString()
			console.log(a)
			console.log(JSON.parse(a))
		}
	}
</script>

<style>

</style>
