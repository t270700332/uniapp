 <template>
	<view>
		<view class="status_bar">
			<!-- 这里是状态栏 -->
		</view>
		<view style="width:100%;"> 
	        <view class="index-header">
	        	<view class="img-view">
	        		<image src="/static/img/logo.png" mode="" id="user-img"></image>
	        	</view>
	        	<view class="user-name-text">
	        	 t270700332
	        	</view>
	        </view>     	
		</view>
		<view class="uni-padding-wrap carousel-wrap">
            <view class="page-section swiper">
                <view class="page-section-spacing">
                    <swiper class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
                        <swiper-item>
                            <view class="swiper-item">
                               <image class="swiper-item-img" src="/static/img/index/swiper1.jpg" mode="" ></image> 
                            </view>
                        </swiper-item>
                        <swiper-item>
                            <view class="swiper-item">
                                <image class="swiper-item-img" src="/static/img/index/swiper2.jpg" mode="" ></image>
                            </view>
                        </swiper-item>
                        <swiper-item>
                            <view class="swiper-item">
                                <image class="swiper-item-img" src="/static/img/index/swiper3.jpg" mode="" ></image>
                            </view>
                        </swiper-item>
                    </swiper>
                </view>
            </view>
        </view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: '我的app',
                autoplay: true,
                interval: 2000,
                indicatorDots: true,
                duration: 500
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


	.carousel-wrap{
        background-color: #274349;
    }

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}

	.index-header {
		width: 100%;
		height: 100upx;
		background-color: #274349;
	}

	.img-view {
		width: 70upx;
		height: 70upx;
        display: inline-block;
        margin-left: 10px;
        margin-top: 10px;
	}

	#user-img {
		width: 100%;
		height: 100%;
		border-radius: 50%;
	}

	.user-name-text {
		width: 100px;
		overflow: hidden; //超出的文本隐藏
		text-overflow: ellipsis; //溢出用省略号显示
		white-space: nowrap; //溢出不换行
		font-size: 16px;
		color: #C0C0C0;
        display: inline-block;
        position: absolute;
        top: 60px;
        left: 60px;
	}

	.status_bar {
		height: var(--status-bar-height);
		width: 100%;
	}
    
    .swiper-item-img{
        width: 100%;
        background-size:100% 100%;
    }
    
</style>
