<template>
	<view class="main_content">
		<view class="uni-margin-wrap">
			<swiper class="swiper" circular :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
				<swiper-item v-for="(item,index) in banner_list">
					<view class="swiper-item uni-bg-red">
						<image :src="getImgPath(item.img)" mode="aspectFill" @error="imageError"></image>
					</view>
				</swiper-item>
				<!-- <swiper-item>
					<view class="swiper-item uni-bg-green"></view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item uni-bg-blue"></view>
				</swiper-item> -->
			</swiper>
		</view>
		
		
		<view class="article_list">
			<view class="article_item" v-for="(item,index) in banner_list" :key="item.banner_id">
				<view class="article_left">
					<image class="article_face" :src="getImgPath(item.img)" mode="aspectFill" @error="imageError"></image>
				</view>
				<view class="article_right">
					<view class="article_title">测试文章标题{{item.title}}</view>
					<view class="article_desc">测试文章详情。。。。。</view>
				</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: '领路君',
				background: ['color1', 'color2', 'color3'],
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				duration: 500,
				banner_list:[],
			}
		},
		onLoad() {
			this.get_banner_list();
		},
		methods: {
			getImgPath(path) {
				return 'http://s1.linglujun.com'+path;
			},
			imageError: function(e) {
				console.error('image发生error事件，携带值为' + e.detail.errMsg)
			},
			get_banner_list: function(){
				uni.request({
				    url: 'http://h5.linglujun.com/api/index/banner',
				    data: {
				        text: 'uni.request'
				    },
				    header: {
				        'custom-header': 'hello' //自定义请求头信息
				    },
				    success: (res) => {
						this.banner_list = res.data.data;
				    },
					complete(res) {
				    	console.log('complatea',res)
				    }
				});
			}
		}
	}
</script>

<style>
	.article_list {
		width: 100%;
		/* background-color: #007AFF; */
	}
	.article_item {
		margin:30rpx 30rpx;
		width: 100%;
		display: flex;
		flex-direction: row;
	}
	.article_item .article_left {
		width: 300rpx;
		height: 150rpx;
	}
	.article_item .article_face {
		width: 100%;
		height: 100%;
		border-radius: 20rpx;
	}
	.article_item .article_right {
		width: 100%;
		padding: 0 0 0 30rpx;
	}
	
	.main_content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	
	.uni-margin-wrap {
		width:690rpx;
		margin:0 30rpx;
	}
	.swiper {
		height: 300rpx;
	}
	.swiper-item {
		display: block;
		height: 300rpx;
		line-height: 300rpx;
		text-align: center;
	}
	
	.swiper-item image {
		width: 100%;
		height: 100%;
	}
	
	.swiper-list {
		margin-top: 40rpx;
		margin-bottom: 0;
	}
	
	.uni-common-mt{
		margin-top:60rpx;
		position:relative;
	}
	
	.info {
		position: absolute;
		right:20rpx;
	}
	
	.uni-padding-wrap {
	    width:550rpx;
	    padding:0 100rpx;
	}
	
</style>
