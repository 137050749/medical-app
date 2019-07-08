<template>
	<view class="content">
		<view class="header">
			<image class="logo" src="/static/images/logo.png"></image>
		</view>
		<view class="item" v-if="list.length>0" v-for="item in list" @tap="toplay" :data-id="item.id" :key="item.id">
			<image class="item-img" :src="item.imgurl" mode=""></image>
			<view class="title">{{item.title}}</view>
		</view>
		<view class="no-more"> 没有更多了 >>> </view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[]
			};
		},
		onLoad() {
			uni.showLoading({
				title: '课程',
				mask: false
			});
			uni.request({
				url: '../../static/data/video.json',
				method: 'GET',
				data: {},
				success: res => {
					this.list = res.data.data
					uni.hideLoading()
				},
				fail: () => {},
				complete: () => {}
			});
		},
		methods:{
			toplay(e) {
				let id = e.currentTarget.dataset.id
				// console.log(id)
				uni.navigateTo({
					url: '../player/player?id=' + id
				})
			}
		}
	}
</script>

<style lang="scss">
	.content{
		width: 90%;
		margin-left: 5%;
		padding-bottom:30upx;
		.header{
			.logo{
				width: 160upx;
				height: 50upx;
				position: fixed;
				top: 20upx;
				left: 20upx;
				z-index: 1000;
			}
		}
		.item{
			width: 45%;
			font-size: 28upx;
			float: left;
			height: 284upx;
			box-shadow: 1upx 1upx 4upx #888;
			margin: 20upx 12upx;
			padding: 4upx;
			.item-img{
				width: 100%;
				height: 200upx;
				
			}
		}
		.no-more{
			width: 100%;
			margin-top:30upx;
			font-size: 24upx;
			color: #ccc;
			text-align: center;
		}
	}
		
</style>
