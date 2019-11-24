<!-- 商品列表组件 <pd-list :list="xx"></pd-list> -->
<template>
	<view class="pd-list">
		<view class="pd-li" v-for="pd in list">
			<view class="" style="width: 16%;position: inherit;top: 34px;">
				<view class="pd-title">{{pd.pdTitle}}</view>
			</view>
			<image class="pd-img" :src="pd.pdImg" mode="widthFix"/>
			<view class="" style="width: 100%;position: inherit;">
				<view class="pd-name">{{pd.pdName}}</view>
			</view>
			<!-- <text class="pd-price">{{pd.pdPrice}} 元</text>
			<text class="pd-sold">已售{{pd.pdSold}}件</text> -->
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			list: { // 数据列表
				type: Array,
				default(){
					return []
				}
			}
		}
	}
</script>

<style>
	/*数据列表*/
	.pd-list{
		margin-top: 10px;
	}
	
	.pd-li{
		position: relative;
		height: 260upx;
		padding: 20upx 16upx 36upx 16upx;
		border-bottom: 1px solid #d6d7d8;
		background-color: #fff0cd;
	}
	.pd-li .pd-img{
		/* position: absolute !important; *//*编译到H5,在list-mescroll-more的案例中需加上!important,解决tab切换过快定位失效的问题*/
		/* left: 36upx;
		top: 20upx; */
		width: 100%;
		height: 100%;
		border-radius: 6px;
	}
	.pd-li .pd-name{
		position: absolute;
		font-size: 26upx;
		overflow: hidden;
		z-index: 2;
		bottom: 0px;
		width: 100%;
		background-color: rgb(103,113,117,0.5);
		bottom: 9px;
		border-bottom-left-radius: 6px;
		border-bottom-right-radius: 6px;
		color: #FFF6DF;
		font-weight: 500;
		padding-left: 10px;
	}
	
	.pd-title{
		position: absolute;
		font-size: 26upx;
		overflow: hidden;
		z-index: 2;
		bottom: 0px;
		width: 100%;
		background-color: rgb(103,113,117,0.5);
		bottom: 9px;
		color: #FFF6DF;
		font-weight: 500;
		border-top-left-radius: 6px;
		text-align:center;
	}
	/* .pd-li .pd-price{
		font-size: 26upx;
		color: red;
	}
	.pd-li .pd-sold{
		font-size: 24upx;
		margin-left: 16upx;
		color: gray;
	} */
</style>
