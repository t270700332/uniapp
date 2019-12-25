<!-- 商品列表组件 <pd-list :list="xx"></pd-list> -->
<template>
	<view class="pd-list">
		<view class="pd-li" v-for="(pd,pdIndex) in list" :key="pd.id">
			<view v-if="pdIndex==0" style="font-size: 40upx;font-weight: 500;padding-top: 20upx;padding-bottom: 20upx;">{{reciveTitle}}</view>
			<view class="pd-user" style="position: relative;">
				<image class="user-image" :src="pd.pdImg"></image>
				<view class="user-info">
					<view>
						<text>{{pd.userName}}</text>
						<text style="float: right;" v-if="pdIndex==0">楼主</text>
						<text style="float: right;" v-if="pdIndex!=0">{{pd.id}}楼</text>
					</view>
					<view>
						<text style="margin-right: 10px;">级别:学徒 </text>
						<text style="margin-right: 10px;">威望:1</text>
						<text>发帖:1568</text>
					</view>
				</view>
			</view>
			<view class="pd-name" v-if="pdIndex==0">{{pd.content}}</view>
			<view class="pd-name" v-if="pdIndex!=0">{{pd.comment}}</view>
			<text class="pd-sold">{{pd.pdSold}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			list: { // 数据列表
				type: Array,
				default () {
					return []
				}
			},
			reciveTitle: {
				type: String
			}
		},
		data() {
			return {
				title: ''
			}
		},
		methods: {}

	}
</script>

<style>
	.pd-list {
		background-color: #fff6df;
	}

	/*数据列表*/
	.pd-li {
		position: relative;
		height: 100%;
		padding: 0upx 0upx 40upx 20upx;
		border-bottom: 1upx solid #eee;
	}

	.pd-li:nth-child(odd) {
		background-color: #fff0cd;
	}

	.pd-li:nth-child(even) {
		background-color: #fff8e7;
	}

	.pd-li .pd-sold {
		font-size: 24upx;
		margin-left: 0px;
		color: gray;
		position: absolute;
		bottom: 0px;
		right: 8px;
	}

	.pd-user {
		border-bottom: 2upx solid #eee;
		border-top: 1upx solid #eee;
	}

	.user-image {
		width: 50px;
		height: 50px;
		border-radius: 50%;
		display: inline-block;
		margin-top: 10px;
		margin-right: 10px;
	}

	.user-info {
		display: inline-block;
		position: absolute;
		top: 10px;
		width: 330px;
	}
</style>
