 <template>
	<view class="content">
		<view class="status_bar">
			<!-- 这里是状态栏 -->
		</view>
		<view style="width: 100%;"> 
	        <view class="index-header">
	        	<view class="img-view">
	        		<image src="/static/img/logo.png" mode="" id="user-img"></image>
	        	</view>
	        	<view class="user-name-text">
	        	 t270700332
	        	</view>
	        </view>     	
		</view>
		<image class="logo" src="/static/img/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: '我的app'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	@import "../../common/css/common.css";

	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		background-color: #fff6df;
		height: 100%;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}

	.index-header {
		width: 100%;
		height: 200upx;
		background-color: #274349;
		position: absolute;
		top: 0;
	}

	.img-view {
		width: 90upx;
		height: 90upx;
		position: absolute;
		top: 55px;
		left: 10px;
	}

	#user-img {
		width: 100%;
		height: 100%;
		border-radius: 50%;
	}

	.user-name-text {
		position: absolute;
		left: 70px;
		top: 70px;
		width: 100px;
		overflow: hidden; //超出的文本隐藏
		text-overflow: ellipsis; //溢出用省略号显示
		white-space: nowrap; //溢出不换行
		font-size: 16px;
		color: #C0C0C0;
	}

	.status_bar {
		height: var(--status-bar-height);
		width: 100%;
	}
</style>
