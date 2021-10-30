<template>
	<view>
		<!-- <u-swiper :list="list" mode='number' :autoplay='false' indicator-pos='bottomRight' height='650'></u-swiper> -->
		<image :src="imageUrl" style="width: 100%;"></image>
		<view class="u-p-20">
			<view class="u-m-b-20">
				<u-tag text="产地量贩" mode="dark" bg-color='#0eb6ff' />
				<text class="u-font-24 u-m-l-20 u-type-info-dark">基地优选 售后无忧</text>
			</view>
			<view class="u-font-36 u-m-b-20">
				{{title}}
			</view>
			<view class="u-m-b-20">
				<text class="u-font-24 u-type-info-dark">入口即化 好吃不腻</text>
			</view>
			<view class="u-m-b-20">
				<text class="prices u-font-36">￥{{prices}}</text>/箱<text
					class="u-type-info-dark line-through u-m-l-25 u-font-24">￥￥{{oldPrices}}</text>
			</view>
			<alert-tips class="u-m-b-10" iconLeft='car' iconColor='#0eb6ff' :content='description'></alert-tips>
			<alert-tips class="u-m-b-10" iconLeft='checkmark-circle' iconColor='#0eb6ff' :content='description2'>
			</alert-tips>
			<alert-tips class="u-m-b-10" iconLeft='info-circle' iconRight='arrow-right' tipsBgColor='#f5ebea'
				iconColor='#ce5f41' :content='description3' @click='onClick'></alert-tips>
			<alert-tips class="u-m-b-10" iconRight='arrow-right' :content='description4' @click='onClick'></alert-tips>
			<view class="evaluate u-p-20">
				<u-section class="u-m-b-20" :show-line='false' title="评价(999)"
					@click="nextEvaluate" sub-title="查看全部"></u-section>
				<evaluate-item></evaluate-item>
			</view>
			<u-divider color="#0eb6ff" height='60' class='u-m-t-20'>详情</u-divider>
			<view class="evaluate  u-p-l-20 u-p-r-20 u-m-t-20">
				<details-item v-for="(item,index) in detailslist" :key='index' :title='item.title'
					:content="item.content"></details-item>
				<view class="u-text-center u-type-info-dark u-p-20" v-if="showMore" @click="nextEcharts">
				    {{lookMore}}
				</view>
			</view>
			
			<view class="u-p-t-20 u-p-b-20">
				<image style="width: 100%;" :src="imageUrl" mode="widthFix"></image>
				<image style="width: 100%;" :src="imageUrl" mode="widthFix"></image>
				<image style="width: 100%;" :src="imageUrl" mode="widthFix"></image>
				<image style="width: 100%;" :src="imageUrl" mode="widthFix"></image>
				<image style="width: 100%;" :src="imageUrl" mode="widthFix"></image>
				<image style="width: 100%;" :src="imageUrl" mode="widthFix"></image>
			</view>
		</view>
		<view class="zhanwei">
		</view>
		<button class="setCart" type="primary" @click="show=true">加入购物车</button>
		<u-popup v-model="show" mode='bottom' closeable>
			<view class="">
				<view class="u-p-30">
					<view class="u-text-center u-font-30">
						<!-- 新疆小苹果 1.5KG -->
						{{title}}
					</view>
					<view class="u-flex u-m-b-20">
						<u-image class='u-m-r-30' width="150rpx" height="150rpx" :src="imageUrl"></u-image>
						<view class="u-flex-col">
							<view class="u-m-b-20">
								<text class="prices">￥{{prices}}</text>/箱 <text
									class="u-m-l-20 through u-type-info-dark u-font-24">￥{{ oldPrices }}</text>
							</view>
							<view class="">
								已选：{{num}}箱
							</view>
						</view>
					</view>
					<view class="u-p-t-20 u-p-b-20 u-border-top">
						商家24H发货，第三方物流配送，免运费
					</view>
					<view class="u-p-t-20 u-p-b-20 u-border-top">
						规格：2.5kg/箱
					</view>
					<view class="u-p-t-20 u-p-b-20 u-border-top u-flex u-row-between">
						<text>购买数量(箱)</text>
						<u-number-box v-model="num" :min="1" @change="valChange"></u-number-box>
					</view>
				</view>
				<button class="" type="primary" @click="show=false">加入购物车</button>
			</view>
		</u-popup>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				num: 1,
				show: false,
				showMore: true,
				prices:'',
				oldPrices:'',
				title: '登高望远',
				imageUrl: '',
				lookMore: '',
				description: '商家24H发货，第三方物流配送，免运费',
				description2: '生鲜不支持7天无理由退货',
				description3: '特价没人限购2份，超出则改商品全部...',
				description4: '已选：2.5kg/箱',
				detailslist: [{
						title: '产地',
						content: '新疆'
					},
					{
						title: '净含量',
						content: '1.5Kg'
					},
					{
						title: '储存条件',
						content: '常温'
					}
				],
				detailslistCopy: [{
						title: '产地',
						content: '新疆'
					},
					{
						title: '净含量',
						content: '1.5Kg'
					},
					{
						title: '储存条件',
						content: '常温'
					},
					{
						title: '产地',
						content: '新疆'
					},
					{
						title: '净含量',
						content: '1.5Kg'
					},
					{
						title: '储存条件',
						content: '常温'
					}
				],
				list: [],
				
			}
		},
		onNavigationBarButtonTap() {
			uni.switchTab({
				url: '/pages/cart/cart'
			})
		},
		methods: {
			goPage(url) {
				uni.navigateTo({
					url: url
				})
			},
			valChange(e) {
				this.num = e.value
			},
			nextEcharts(e) {
				// this.showMore = true
				this.detailslist = this.detailslistCopy
				// var listItem = JSON.stringify((this.detailslistCopy))
				//默认跳转方式
				// uni.navigateTo({
				// 	url: '../echartsVue/echartsVue?text='+ this.lookMore +'&listArr'+ listItem
				// });
				//跳转到更多页面要使用下面方法
				uni.switchTab({
				    url: '../echartsVue/echartsVue?listArr'
				});
			},
			nextEvaluate(e){
				let arr = [{
						title: '产地',
						content: '新疆'
					},
					{
						title: '净含量',
						content: '1.5Kg'
					},
					{
						title: '储存条件',
						content: '常温'
					}]
				
				let listItem = JSON.stringify(arr)
				uni.navigateTo({
					url: '../evaluate/evaluate?arrItem='+ listItem
				})
			},
			onClick() {
				this.$toast('被点击了')
			}
		},
		onLoad(param) {
			this.title = param.title
			this.imageUrl = param.imageUrl
			this.prices = param.prices
			this.oldPrices = parseInt(param.prices) + 500;
			this.lookMore = '查看更多'
		}
	}
</script>

<style scoped>
	.prices {
		color: red;
	}

	.through {
		text-decoration: line-through;
	}

	.setCart {
		position: fixed;
		bottom: 0;
		left: 0;
		width: 100%;
	}

	.zhanwei {
		height: 50rpx;
	}

	.evaluate {
		background-color: #F5F5F5;
		border-radius: 8rpx;
	}

	.line-through {
		text-decoration: line-through
	}

	.prices {
		color: #ce5962;
	}
	.chart-title-text{
		text-align: center;
		font-size:32rpx;
		margin-bottom: 10rpx;
	}
</style>
