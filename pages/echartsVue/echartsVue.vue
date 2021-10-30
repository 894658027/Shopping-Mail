<template>
	<view>
		<view class="u-text-center u-type-info-dark u-p-20">
			<!-- {{text}} -->
			
			<!-- 引入echarts 柱形图 -->
			<view class="charts-box">
				<qiun-data-charts type="column" :chartData="chartData_column" />
			</view>
			<view class="chart-title-text">柱形统计图</view>
			<u-line color="gray" class="lineMargin"></u-line>
			
			<!-- 引入echarts 饼图 -->
			<view class="charts-box">
				<qiun-data-charts type="pie" :chartData="chartData_pie" background="none" />
			</view>
			<view class="chart-title-text">饼状统计图</view>
			<u-line color="gray" class="lineMargin"></u-line>
			
			<!-- 引入echarts 环形图 -->
		<!-- 	<view class="charts-box">
				<qiun-data-charts type="ring" :chartData="chartData_ring" background="none" />
			</view>
			<view class="chart-title-text">环形统计图</view>	
			<u-line color="gray" class="lineMargin"></u-line> -->
			
		</view>

		<u-tabbar :list="tabbar" :mid-button="true"></u-tabbar>
	</view>

</template>

<script>
	export default {
		data() {
			return {
				text: '',
				tabbar: '',
				// echars-data数据内容
				chartData_column: {
					categories: ["2016", "2017", "2018", "2019", "2020", "2021"],
					series: [{
						name: "目标销售值(万)",
						data: [35, 36, 31, 33, 13, 34]
					}, {
						name: "实际销售值(万)",
						data: [18, 27, 21, 24, 6, 28]
					}]
				},
				chartData_pie: {
					series: [{
						data: [{
							name: "东北",
							value: 50
						}, {
							name: "华北",
							value: 30
						}, {
							name: "华中",
							value: 20
						}, {
							name: "华南",
							value: 18
						}, {
							name: "云贵",
							value: 8
						}]
					}]
				},
				chartData_ring: {
					series: [{
						data: [{
							name: "东北",
							value: 50
						}, {
							name: "华北",
							value: 30
						}, {
							name: "华中",
							value: 20
						}, {
							name: "华南",
							value: 18
						}, {
							name: "云贵",
							value: 8
						}]
					}]
				}
			}
		},
		methods: {

		},
		onLoad(param) {
			this.text = param.text
			console.log((param))
			
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
			
		}
	}
</script>

<style>
	.lineMargin{
		/* margin-bottom: 40rpx; */
		margin: 40rpx,0rpx,0rpx,40rpx;
	}
	.chart-title-text{
		text-align: center;
		font-size:32rpx;
		margin-bottom: 20rpx;
	}


</style>
