 <template>
<mescroll-uni :down="downOption" @down="downCallback" :up="upOption" @up="upCallback" @init="mescrollInit">
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
		<view class="carousel-wrap">
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
		<view calss="uni-padding-wrap uni-common-mt nga-lanmu" style="background-color: #fff0cd;height: 115px;">
			 <view class="uni-flex uni-row">
				<view class="flex-item uni-bg-1">
					<image class="swiper-item-img" src="/static/img/index/default.png" style="height: 60px;width: 60px;"></image>
					栏目</view>
				<view class="flex-item uni-bg-2">
					<image class="swiper-item-img" src="/static/img/index/default.png" style="height: 60px;width: 60px;"></image>
					评分</view>
				<view class="flex-item uni-bg-3">
					<image class="swiper-item-img" src="/static/img/index/default.png" style="height: 60px;width: 60px;"></image>
					赛事</view>
				<view class="flex-item uni-bg-4">
					<image class="swiper-item-img" src="/static/img/index/default.png" style="height: 60px;width: 60px;"></image>
					组队</view>
				<view class="flex-item uni-bg-5">
					<image class="swiper-item-img" src="/static/img/index/default.png" style="height: 60px;width: 60px;"></image>
					发现</view>
			 </view>
		</view>
		
		<view calss="uni-padding-wrap uni-common-mt" style="background-color: #fff0cd;">
			 <view class="uni-title uni-common-mt" style="margin-top: 10px;padding: 0 0;position: relative;">
				 <image src="/static/img/index/index.png" style="width: 20px;height: 20px;margin-left: 8px;position: absolute;top: 8px;"></image>
				 <text style="font-size: 16px;color: black;font-weight: 600;margin-left: 10px;position: absolute;left: 25px;top: 7px;">论坛热点</text>
				 <image src="/static/img/index/suiji.png" style="width: 20px;height: 20px;right: 10px;position: absolute;top: 8px;"></image>
			 </view>
			 <hotNoteList></hotNoteList>
		</view>
	<pd-list :list="pdList"></pd-list>
	</view>
	</mescroll-uni>
</template>

<script>
	import hotNoteList from "../../components/index/hotNoteList.vue";
	import MescrollUni from "../../components/mescroll-uni/mescroll-uni.vue";
	import PdList from "../../components/index/pd-list.vue";
	import mockData from "../../common/js/pdlist.js"; // 模拟数据
	
	export default {
		components: {
		      hotNoteList,
			  MescrollUni,
			  PdList
		},
		data() {
			return {
				mescroll: null, //mescroll实例对象
				title: '我的app',
                autoplay: true,
                interval: 2000,
                indicatorDots: true,
                duration: 500,
				// 下拉刷新的常用配置
				downOption: { 
					use: false, // 是否启用下拉刷新; 默认true
					auto: true, // 是否在初始化完毕之后自动执行下拉刷新的回调; 默认true
					autoShowLoading: false, // 如果设置auto=true(在初始化完毕之后自动执行下拉刷新的回调),那么是否显示下拉刷新的进度; 默认false
					isLock: false, // 是否锁定下拉刷新,默认false;
					offset: 80, // 在列表顶部,下拉大于80upx,松手即可触发下拉刷新的回调
					fps: 40, // 下拉节流 (值越大每秒刷新频率越高)
					inOffsetRate: 1, // 在列表顶部,下拉的距离小于offset时,改变下拉区域高度比例;值小于1且越接近0,高度变化越小,表现为越往下越难拉
					outOffsetRate: 0.2, // 在列表顶部,下拉的距离大于offset时,改变下拉区域高度比例;值小于1且越接近0,高度变化越小,表现为越往下越难拉
					bottomOffset: 20, // 当手指touchmove位置在距离body底部20upx范围内的时候结束上拉刷新,避免Webview嵌套导致touchend事件不执行
					minAngle: 45, // 向下滑动最少偏移的角度,取值区间  [0,90];默认45度,即向下滑动的角度大于45度则触发下拉;而小于45度,将不触发下拉,避免与左右滑动的轮播等组件冲突;
					textInOffset: '下拉刷新', // 下拉的距离在offset范围内的提示文本
					textOutOffset: '释放更新', // 下拉的距离大于offset范围的提示文本
					textLoading: '加载中 ...' // 加载中的提示文本
				},
				// 上拉加载的常用配置
				upOption: {
					use: true, // 是否启用上拉加载; 默认true
					auto: true, // 是否在初始化完毕之后自动执行上拉加载的回调; 默认true
					isLock: false, // 是否锁定上拉加载,默认false;
					isBoth: true, // 上拉加载时,如果滑动到列表顶部是否可以同时触发下拉刷新;默认true,两者可同时触发;
					isBounce: false, // 默认禁止橡皮筋的回弹效果, 必读事项: http://www.mescroll.com/qa.html?v=190725#q25
					page: {
						num: 0, // 当前页码,默认0,回调之前会加1,即callback(page)会从1开始
						size: 10, // 每页数据的数量
						time: null // 加载第一页数据服务器返回的时间; 防止用户翻页时,后台新增了数据从而导致下一页数据重复;
					},
					noMoreSize: 3, // 如果列表已无数据,可设置列表的总数量要大于等于5条才显示无更多数据;避免列表数据过少(比如只有一条数据),显示无更多数据会不好看
					offset: 10, // 距底部多远时,触发upCallback
					textLoading: '加载中 ...', // 加载中的提示文本
					textNoMore: '-- END --', // 没有更多数据的提示文本
					toTop: {
						// 回到顶部按钮,需配置src才显示
						src: "http://www.mescroll.com/img/mescroll-totop.png", // 图片路径
						offset: 1000, // 列表滚动多少距离才显示回到顶部按钮,默认1000
						duration: 300 // 回到顶部的动画时长,默认300ms
					},
					empty: {
						use: true, // 是否显示空布局
						icon: "http://www.mescroll.com/img/mescroll-empty.png", // 图标路径
						tip: '~ 暂无相关数据 ~', // 提示
						btnText: '去逛逛 >', // 按钮
						fixed: false, // 是否使用fixed定位,默认false; 配置fixed为true,以下的top和zIndex才生效
						top: "35%", // fixed定位的top值 (完整的单位值,如 "35%"; "300upx")
						zIndex: 99 // fixed定位z-index值
					},
					onScroll: true // 是否监听滚动事件, 默认false (配置为true时,可@scroll="scroll"获取到滚动条位置和方向)
				},
				// 列表数据
				pdList: [],
			}
		},
		onLoad() {

		},
		methods: {
			// mescroll组件初始化的回调,可获取到mescroll对象
			mescrollInit(mescroll) {
				this.mescroll = mescroll;
			},
			downCallback(mescroll){
				mescroll.endSuccess()
			},
			upCallback(mescroll) {
				//联网加载数据
				this.getListDataFromNet(mescroll.num, mescroll.size, (curPageData)=>{
					//联网成功的回调,隐藏下拉刷新和上拉加载的状态;
					//mescroll会根据传的参数,自动判断列表如果无任何数据,则提示空;列表无下一页数据,则提示无更多数据;
					console.log("mescroll.num=" + mescroll.num + ", mescroll.size=" + mescroll.size + ", curPageData.length=" + curPageData.length);
				
					//方法一(推荐): 后台接口有返回列表的总页数 totalPage
					//mescroll.endByPage(curPageData.length, totalPage); //必传参数(当前页的数据个数, 总页数)
				
					//方法二(推荐): 后台接口有返回列表的总数据量 totalSize
					//mescroll.endBySize(curPageData.length, totalSize); //必传参数(当前页的数据个数, 总数据量)
				
					//方法三(推荐): 您有其他方式知道是否有下一页 hasNext
					//mescroll.endSuccess(curPageData.length, hasNext); //必传参数(当前页的数据个数, 是否有下一页true/false)
				
					//方法四 (不推荐),会存在一个小问题:比如列表共有20条数据,每页加载10条,共2页.如果只根据当前页的数据个数判断,则需翻到第三页才会知道无更多数据
					mescroll.endSuccess(curPageData.length);
					//设置列表数据
					if(mescroll.num == 1) this.pdList = []; //如果是第一页需手动制空列表
					this.pdList=this.pdList.concat(curPageData); //追加新数据
					
				}, () => {
					//联网失败的回调,隐藏下拉刷新的状态
					mescroll.endErr();
				})
			},
			/*联网加载列表数据
			在您的实际项目中,请参考官方写法: http://www.mescroll.com/uni.html#tagUpCallback
			请忽略getListDataFromNet的逻辑,这里仅仅是在本地模拟分页数据,本地演示用
			实际项目以您服务器接口返回的数据为准,无需本地处理分页.
			* */
			getListDataFromNet(pageNum,pageSize,successCallback,errorCallback) {
				//延时一秒,模拟联网
				setTimeout(()=> {
					try{
						let listData = []
						for (let k = 0; k < mockData.length; k++) {
							listData.push(mockData[k])
						}
						console.log(listData)
						// 回调
						successCallback && successCallback(listData);
					} catch (e) {
						//联网失败的回调\
						console.log(11)
						errorCallback && errorCallback();
					}
				},1000)
			}
		}
	}
</script>

<style>
	@import "../../common/css/common.css";

    uni-page-body{
		background-color: #591804;
    }
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		background-color: #fff6df;
		height: 100%;
	}


	.carousel-wrap{
		background: linear-gradient(to top, #fff0cd 50%, #274349 50%);
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
        border-radius: 10px;
        height: 190px;
    }
    
    .swiper{
      height: 200px;
     }  
    .swiper-item{
        padding-left: 10px;
        padding-right: 10px;
        padding-top: 5px;
    }
	
	.flex-item {
		margin-top:15px ;
		width: 20%;
		height: 60px;
		text-align: center;
		/* line-height: 150px; */
		border-radius: 10px;
		background-color: #555555;
	}
	
	.uni-bg-1{
		margin-left: 2%;
		margin-right: 4%;
	}
	.uni-bg-2{
		margin-right: 4%;
	}
	.uni-bg-3{
		margin-right: 4%;
	}
	.uni-bg-4{
		margin-right: 4%;
	}
	.uni-bg-5{
		margin-right: 2%;
	} 
	
	.uni-title{
		height: 40px;
	    border-bottom: 1px solid #d6d7d8;
	}
	
</style>
