<template>
	<view class="app_content">
		
		<view class="uni-margin-wrap">
			<swiper class="swiper" circular :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
				<swiper-item>
					<view class="swiper-item uni-bg-red">A</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item uni-bg-green">B</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item uni-bg-blue">C</view>
				</swiper-item>
			</swiper>
		</view>
		
		<view class="index_article_list">
			<view class="item">
				<view class="item_l">
					<image src="http://api.uniapp.com/upload/banner/banner_1.jpg" mode="aspectFill"></image>
				</view>
				<view class="item_r">
					<view class="article_title">文章标题</view>
					<view class="article_desc">文章简介文章简介文章简介文章简介文章简介文章简介文章简介
					文章简介文章简介文章简介文章简介文章简介文章简介文章简介文章简介文章简介文章简介文章简介文章简介
					</view>
				</view>
			</view>
			<view class="item">
				<view class="item_l">
					<image src="http://api.uniapp.com/upload/banner/banner_2.jpg" mode="aspectFill"></image>
				</view>
				<view class="item_r">
					<view class="article_title">文章标题</view>
					<view class="article_desc">文章简介文章简介文章简介文章简介文章简介文章简介文章简介
					文章简介文章简介文章简介文章简介文章简介文章简介文章简介文章简介文章简介文章简介文章简介文章简介
					</view>
				</view>
			</view>
			<view class="item">
				<view class="item_l">
					<image src="http://api.uniapp.com/upload/banner/banner_3.jpg" mode="aspectFill"></image>
				</view>
				<view class="item_r">
					<view class="article_title">文章标题</view>
					<view class="article_desc">文章简介文章简介文章简介文章简介文章简介文章简介文章简介
					文章简介文章简介文章简介文章简介文章简介文章简介文章简介文章简介文章简介文章简介文章简介文章简介
					</view>
				</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				background: ['color1', 'color2', 'color3'],
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
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
	.app_content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.uni-margin-wrap {
		width:690rpx;
		margin:30rpx 30rpx 0 30rpx;
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
	
	.index_article_list {
		width:690rpx;
		margin:30rpx 30rpx 0 30rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	
	.item {
		width: 100%;
		height: auto;
		display: flex;
		flex-direction: row;
		margin-bottom: 30rpx;
	}
	
	.item .item_l {
		width: 30%;
	}
	
	.item .item_l image {
		width: 100%;
		height: 100%;
	}
	
	.item .item_r {
		width: 65%;
		display: flex;
		flex-direction: column;
		margin-left:30rpx;
	}
	
	.item .item_r .article_title {
		display: -webkit-box;
		overflow: hidden;
		white-space: normal !important;
		text-overflow: ellipsis;
		word-wrap: break-word;
		-webkit-line-clamp: 1;
		-webkit-box-orient: vertical
	}
	
	.item .item_r .article_desc {
		display: -webkit-box;
		overflow: hidden;
		white-space: normal !important;
		text-overflow: ellipsis;
		word-wrap: break-word;
		-webkit-line-clamp: 3;
		-webkit-box-orient: vertical
	}
	
	
	
</style>
