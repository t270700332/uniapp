<!-- 商品列表组件 <pd-list :list="xx"></pd-list> -->
<template>
	<view class="pd-list">
		<view class="pd-li" v-for="pd in list" :key="pd.id"  @click="toContent(pd.pdName)">
			<view class="pd-name">{{pd.pdName}}</view>
			<text class="pd-price">{{pd.pdPrice}}</text>
			<text class="pd-number">{{pd.pdNumber}}</text>
			<text class="pd-sold">{{pd.pdSold}}</text>
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
		},
		methods:{
			toContent(title){
			  uni.navigateTo({
			  	url:'../../pages/shequ/content?title='+title,
			  })
			}
		}
		
	}
</script>

<style>
	.pd-list{
		background-color: #fff6df;
	}
	/*数据列表*/
	.pd-li{
		position: relative;
		height: 100%;
		padding: 20upx 16upx 0upx 20upx;
		border-bottom: 1upx solid #eee;
	}
	.pd-li .pd-name{
		font-size: 26upx;
		/* line-height: 40upx; */
		height: 100%;
		margin-bottom: 20upx;
		overflow: hidden;
	}
	.pd-li .pd-price{
		font-size: 26upx;
		color: gray;
	}
	.pd-li .pd-sold{
		font-size: 24upx;
		margin-right: 60upx;
		color: gray;
		float: right;
	}
	
	.pd-number{
		float: right;
		font-size: 24upx;
		margin-right: 10upx;
		color: gray;
	}
</style>
