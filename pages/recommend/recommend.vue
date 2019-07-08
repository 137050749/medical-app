<template>
	<view class="content">
		<view class="header">
			<image class="logo" src="/static/images/logo.png"></image>
		</view>
		<view class="play-title">
			{{title}}
		</view>
		<video :src="playerurl" class="player" controls="controls"></video>
		<view class="desc-title">视频介绍</view>
		<view class="desc">
			{{desc}}
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				playerurl: '',
				desc: '',
				title:'',
				index:-1
			}
		},
		onLoad(option) {
			console.log(option)
			if(option){
				this.index = option.recommendid
				console.log(this.index)
			}
			uni.request({
				url: '../../static/data/recommend.json',
				method: 'GET',
				data: {},
				success: (res) => {
					console.log(res)
					this.playerurl = res.data.data[this.index].playurl
					this.title = res.data.data[this.index].title
					this.desc = res.data.data[this.index].desc
				},
				fail: (err) => confirm("网络连接超时"),
				complete: () => {}
			})			
		},
		methods: {
			
		}
	}
</script>

<style lang="scss" scoped>
	.content{
		width: 100%;
		.header{
			.logo{
				width: 160upx;
				height: 50upx;
				position: fixed;
				top: 20upx;
				left: 40%;
				z-index: 1000;
			}
		}
		.play-title{
			font-size: 32upx;
			padding: 40upx;
			font-weight: 800;
		}
		.player{
			width: 90%;
			margin-left: 5%;
		}
		.desc-title{
			font-size: 28upx;
			font-weight: 800;
			padding-left:40upx;
		}
		.desc{
			font-size: 32upx ;
			color: #999999;
			padding: 20upx 40upx;
		}
	}
</style>
