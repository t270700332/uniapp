<template name="hotNoteList">
	<view class="uni-flex uni-column">
		 <view class="flex-item flex-item-V note-list">
			 <view class="note-img-view">
			 	<image class="note-img" src="../../static/img/index/list1.png"></image>
			 </view>
			 <view class="note-content">
				 <view class="note-title" style="padding-right: 10px;text-align: left;">
					 [副本讨论]LM骑士和BL萨满，一边是王者无敌，一边是移动荣誉？事实到底是什么样的。。。</view>
				 <view class="note-information">
					 <view class="note-information-text">经典旧世</view>
					 <view class="note-information-text">次郎</view>
					 <view class="note-information-text">99</view>
				 </view>
			 </view>
		 </view>
		 <view class="flex-item flex-item-V note-list">
			 <view class="note-img-view">
			 	<image class="note-img" src="../../static/img/index/list2.png"></image>
			 </view>
			 <view class="note-content">
			 	<view class="note-title" style="padding-right: 10px;text-align: left;">
			 		明日方舟-罗德岛驻艾泽拉斯大使馆
				</view>
			 	<view class="note-information">
					 <view class="note-information-text">艾泽拉斯议事厅</view>
					 <view class="note-information-text">今天我没哭</view>
					 <view class="note-information-text">99</view>
			 	</view>
			 </view>
		 </view>
		 <view class="flex-item flex-item-V note-list">
			 <view class="note-img-view">
			 	<image class="note-img" src="../../static/img/index/list1.png"></image>
			 </view>
			 <view class="note-content">
			 	<view class="note-title" style="padding-right: 10px;text-align: left;">
			 		[FPX战队]冠军中野双排了
				</view>
			 	<view class="note-information">
					 <view class="note-information-text">赛况实况分析</view>
					 <view class="note-information-text">请不要放弃</view>
					 <view class="note-information-text">130</view>
			 	</view>
			 </view>
		 </view>
		 <view class="flex-item flex-item-V note-list">
			<view class="note-img-view">
				<image class="note-img" src="../../static/img/index/list2.png"></image>
			</view>
			<view class="note-content">
				<view class="note-title" style="padding-right: 10px;text-align: left;">
				  有人要病毒精灵吗	
				</view>
				<view class="note-information">
					 <view class="note-information-text">精灵宝可梦系列</view>
					 <view class="note-information-text">pymtc</view>
					 <view class="note-information-text">199</view>
				</view>
			</view>	 
		 </view>
	</view>
</template>

<script>
	export default {
		name:"hotNoteList",
		data() {
			return {
				
			};
		}
	}
</script>

<style>
.flex-item-V {
	width: 100%;
	width: 100%;
	height: 70px;
	line-height: 70px;
	margin-top: 0PX;
	border-radius: 0PX;
	background-color: #fff0cd;
}

.note-img-view{
	width: 20%;
	display: inline-block;
	margin-top: 10px;
}

.note-content{
   width: 80%;
   display: inline-block;
}

.note-img{
	height: 50px;
	width: 50px;
	border-radius: 50px;
}

.note-list{
	border-bottom: 1px solid #d6d7d8;
}

.note-title{
  font-size: 12px;
  height: 45px;
  line-height: 45px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}	

.note-information{
  height: 15px;
}

.note-information-text{
  font-size: 10px;
  width: 32%;
  display:inline-block;
}

.note-information-text:first-child{
	text-align: left;
}

.note-information-text:nth-child(2){
	text-align: center;
}

.note-information-text:nth-child(3){
	text-align: right;
	margin-right:10px;
}
</style>
