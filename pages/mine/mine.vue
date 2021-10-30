<template>
	<view class="">
		<view class="top-bg"></view>
		<view class="u-p-20 page">
			<view class="user-box u-p-l-20 u-p-b-20 u-p-r-20">
				<view class="user-info u-p-l-20 u-p-t-20 u-p-r-20">
					<view class="u-flex u-row-between">
						<view class="u-flex">
							<u-image width="100rpx" height="100rpx" shape="circle" src="/static/logo.png"></u-image>
							<view class="u-p-20 u-type-primary">
								韩東東
							</view>
						</view>
						<view class="u-flex">
							<u-icon name="scan" class='u-m-r-20' color="#2979ff" size="40"></u-icon>
							<u-image width="60rpx" height="60rpx" shape="circle" src="/static/icon/qr.png"></u-image>
						</view>
					</view>
					<u-grid :col="3" :border='false'>
						<u-grid-item>
							<view class="">
								3
							</view>
							<view class="u-type-info-dark">
								优惠券
							</view>
						</u-grid-item>
						<u-grid-item>
							<view class="">
								100.00
							</view>
							<view class="u-type-info-dark">
								我的账户
							</view>
						</u-grid-item>
						<u-grid-item>
							<view class="">
								3
							</view>
							<view class="u-type-info-dark">
								电子券
							</view>
						</u-grid-item>
					</u-grid>
				</view>
			</view>
			<u-gap height="165"></u-gap>
			<view class="box">
				<view class="u-p-20 u-border-bottom">
					我的订单
				</view>
				<u-grid :col="4" :border='false'>
					<u-grid-item>
						<u-icon name="tags" :size="46" color="#0eb6ff"></u-icon>
						<view class="u-type-info-dark">待付款</view>
					</u-grid-item>
					<u-grid-item>
						<u-badge count="3" :offset="[20, 20]"></u-badge>
						<u-icon name="car" :size="46" color="#0eb6ff"></u-icon>
						<view class="u-type-info-dark">待发货</view>
					</u-grid-item>
					<u-grid-item>
						<u-icon name="email" :size="46" color="#0eb6ff"></u-icon>
						<view class="u-type-info-dark">待收货</view>
					</u-grid-item>
					<u-grid-item>
						<u-icon name="thumb-up" :size="46" color="#0eb6ff"></u-icon>
						<view class="u-type-info-dark">待评价</view>
					</u-grid-item>
				</u-grid>
			</view>
			<u-gap height="20"></u-gap>
			<view class="box">
				<view class="u-p-20 u-border-bottom">
					常用工具
				</view>
				<u-grid :col="4" :border='false'>
					<u-grid-item>
						<u-icon name="coupon-fill" :size="46" color="#ce5f41"></u-icon>
						<view class="u-type-info-dark">开发票</view>
					</u-grid-item>
					<u-grid-item>
						<u-icon name="star-fill" :size="46" color="#ffe38f"></u-icon>
						<view class="u-type-info-dark">收藏内容</view>
					</u-grid-item>
				</u-grid>
			</view>
			<u-gap height="20"></u-gap> 
			<u-divider color="#0eb6ff" height='60' class='u-m-b-10' bg-color="#f5f5f5">推荐</u-divider>
			<view class="u-m-t-20 u-flex u-flex-wrap u-row-between">
				<index-list-item v-for="(item,index) in recommendList" :key='index' class="u-m-b-20 recommend-item itemBox" vertical :item='item'>
					<!-- <image src=></image> -->
					<image class="imgBox" :src="item.url" ></image>
					<view class="demo-title">
						{{item.name}}
					</view> 
					<view class="demo-price">  
						{{item.prices}}元
					</view>
					<view class="demo-tag">
						<view class="demo-tag-owner">
							自营
						</view>
						<view class="demo-tag-text">
							放心购
						</view>
					</view>
					<!-- <view class="demo-shop">
						{{item.shop}}
					</view> -->
				</index-list-item>
			</view>
			<u-loadmore :status="status" />
		</view>
		<u-tabbar :list="tabbar" :mid-button="true"></u-tabbar> 
	</view>
</template>

<script>
	import {
		goodsList
	} from '@/common/data/data.js'
	export default {
		data() {
			return {
				show: false,
				tabbar: '',
				status: 'loadmore',
				recommendList: [],
			};
		},
		onNavigationBarButtonTap(e) {
			console.log(e.index)
			switch (e.index) {
				case 0:
					this.$toast('点击了设置')
					break;
				default:
					this.$toast('点击了客服')
					break;
			}
		},
		onLoad() {
			this.recommendList = goodsList
			this.tabbar = [{
					iconPath: "/static/tabbar/home2.png",
					selectedIconPath: "/static/tabbar/home.png",
					text: '首页',
					// count: 2,
					// isDot: true,
					pagePath: "/pages/index/index"
				},
				{
					iconPath: "/static/uview/example/js.png",
					selectedIconPath: "/static/uview/example/js_select.png",
					text: '图表页',
					midButton: true,
					pagePath: "/pages/echartsVue/echartsVue"
				},
				{
					iconPath: "/static/tabbar/mine2.png",
					selectedIconPath: "/static/tabbar/mine.png",
					text: '个人中心',
					pagePath: "/pages/mine/mine"
				},
			]
		},
		methods: {

		},
	}
</script>

<style scoped lang="scss">
	page {
		background-color: #F5F5F5;
	}

	.box {
		background-color: #FFFFFF;
	}

	.user-box {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
	}

	.user-info {
		background-color: #FFFFFF;
		z-index: 333;
		border-radius: 8rpx;
		border-bottom: 10rpx solid #0eb6ff;
		box-shadow: 0 0 15rpx #cacaca;
	}

	.top-bg {
		// background-color: #0eb6ff;
		height: 100rpx;
	}

	.page {
		background-color: #F5F5F5;
	}

	.recommend-item {
		width: 48%;
	}
	.demo-title {
		font-size: 30rpx;
		margin-top: 5px;
		color: $u-main-color;
		margin-left: 10rpx;
	}
	.demo-price {
		font-size: 30rpx;
		color: $u-type-error;
		margin-top: 5px;
		margin-left: 10rpx;
	}
	.demo-tag {
		display: flex;
		margin-top: 5px;
		margin-left: 5rpx;
	}
	
	.demo-tag-owner {
		background-color: $u-type-error;
		color: #FFFFFF;
		display: flex;
		align-items: center;
		padding: 4rpx 14rpx;
		border-radius: 50rpx;
		font-size: 20rpx;
		line-height: 1;
	}
	
	.demo-tag-text {
		border: 1px solid $u-type-primary;
		color: $u-type-primary;
		margin-left: 10px;
		border-radius: 50rpx;
		line-height: 1;
		padding: 4rpx 14rpx;
		display: flex;
		align-items: center;
		border-radius: 50rpx;
		font-size: 20rpx;
	}
	.demo-shop {
		font-size: 22rpx;
		color: $u-tips-color;
		margin-top: 5px;
	}
	.itemBox{
		background: #FFFFFF;
		border-radius: 10px;
		padding-bottom: 10px;
	}
	.imgBox{
		width: 250rpx;
		height: 250rpx; 
		margin: 0rpx auto;
		display: block;
	}
</style>
