<template>
	<view>
		<view class="header">
			<image class="logo" src="/static/images/logo.png"></image>
		</view>
		<view class="loaded" v-if="isShow">
			<view class="person-info"> 
				<image class="photo" src="../../static/images/defaultphoto.png" mode=""></image>
				<view class="person-name" @click="toloading">{{username ? `欢迎${username}登录` : '请立即登录'}} </view>
				<view class="exitBtn" v-if="btnShow" @click="handleExit">退出</view>
			</view>
			<hr>
			<view class="course-item" >
				<view class="focus-title">你关注的课程</view>
				<view class="boutique" v-if="username">
					<scroll-view class="scroll-view_H" scroll-x="true" @scroll="scroll" scroll-left="0">
						<view class="course-info scroll-view-item_H" v-for="item in focusPlaylist"
						 :key="item.id" @tap="toPlayerPage" :data-focusid="item.id">
							<view>
								<image class="course-img" :src="item.imgurl" mode=""></image>
								<view class="course-name">{{item.title}}</view>
							</view>
						</view>
					</scroll-view>
				</view>
			</view>
			<view class="course-item">
				<view class="focus-title">热门推荐</view>
				<view class="boutique">
					<scroll-view class="scroll-view_H" scroll-x="true" @scroll="scroll" scroll-left="0">
						<view v-for="item in hotPlaylist" :key="item.id" class="course-info scroll-view-item_H"
						@tap="toRecommendPlayerPage" :data-recommendid="item.id">
							<view>
								<image class="course-img" :src="item.imgurl" mode=""></image>
								<view class="course-name">{{item.title}}</view>
							</view>
						</view>
					</scroll-view>
				</view>
			</view>
		</view>
		<view class="unloading" v-if="!isShow">
			<view class="loading-info"> 
				<view class="loading-input">
					<input @blur="getUsernameValue" type="text" value="" placeholder="请输入您的账号"/><br>
					<input @blur="getPasswordValue" type="password" value="" placeholder="请输入您的密码" />
					<button type="primary" @click="loading">登录</button>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				username:null,
				password:null,
				isShow:true,
				btnShow:true,
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				duration: 500.,
				scrollTop: 0,
				old: {
					scrollTop: 0
				},
				focusPlaylist: [],
				hotPlaylist: []
			};
		},
		onLoad() {
			uni.request({
				url: '../../static/data/focus.json',
				method: 'GET',
				data: {},
				success: (res) => {
					this.focusPlaylist = res.data.data
				},
				fail: (err) => confirm("网络连接超时"),
				complete: () => {}
			})
			uni.request({
				url: '../../static/data/recommend.json',
				method: 'GET',
				data: {},
				success: (res) => {
					this.hotPlaylist = res.data.data
				},
				fail: (err) => confirm("网络连接超时"),
				complete: () => {}
			})			
		},
		methods:{
			getUsernameValue(e) {
				this.username = e.detail.value
			},
			getPasswordValue(e) {
				this.password = e.detail.value
			},
			loading() {
				this.username && this.password ? this.isShow = true : this.isShow = false;	
			},
			handleExit() {
				this.username = null
				this.password = null
				this.btnShow = false
			},
			toloading() {
				if (!this.username) {
					this.isShow = false
				}				
				this.btnShow = true
			},
			toPlayerPage(e) {
				console.log(e.currentTarget.dataset.focusid)
				let id = e.currentTarget.dataset.focusid
				uni.navigateTo({
					url: '../focus-course/focus-course?focusid=' + id
				})
			},
			toRecommendPlayerPage(e) {
				console.log(e)
				let id = e.currentTarget.dataset.recommendid
				console.log(id)
				uni.navigateTo({
					url: '../recommend/recommend?recommendid=' + id
				})
			},
			scroll(e) {
				this.old.scrollTop = e.detail.scrollTop
			},
		}
	}
</script>

<style lang="scss" scoped>
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
	.loaded{
		.person-info{
			display: flex;
			width: 90%;
			margin-left: 5%;
			margin-top: 100upx;
			padding-bottom: 60upx;
			.photo{
				width: 80upx;
				height: 80upx;
				border-radius: 50%;
				border: 6upx solid #1296db;
				padding: 10upx;
				overflow: hidden;
				margin-right: 80upx;
			}
			.person-name{
				font-size: 32upx;
				color: #999;
				font-weight: 600;
				line-height: 100upx;
			}
			.exitBtn{
				height: 60upx;
				padding:0 20upx;
				margin-top: 20upx; 
				text-align: center;
				vertical-align: center;
				line-height: 60upx;
				font-size: 32upx;
				color: #999;
				position: relative;
				left: 140upx;
				top: 0;
			}	
		}
	}
	.unloading{
		background-color: rgba(0,0,0,.5);
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		padding: 40upx;
		.loading-info{
			width: 90%;
			background-color: #fff;
			border: 4upx solid #1296db;
			position: relative;
			top: 200upx;
			padding: 30upx;
			border-radius: 10upx;
			.loading-input{
				input{
					border: 1px solid #999;
					font-size: 24upx;
					border-radius: 6upx;
					display: inline-block;
					margin: 30upx 0;
					width: 100%;
				}
				button{
					margin-bottom: 30upx;
				}
			}
		}
	}	
	.focus-title{
		font-size: 28upx;
		padding: 20upx 0 0 20upx;
	}
	.scroll-view_H{
		box-sizing: border-box;
		width: 100%;
		white-space: nowrap;	
	}
	.scroll-view-item_H {
		display: inline-block;
		width: 100%;
		height: 260upx;
		text-align: center;
		font-size: 36upx;
	}
	.course-name{
		width: 100%;
		font-size: 24upx;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
	}
	.course-img{
		width: 100%;
		height: 180upx;
	}
	.course-info{
		width: 300upx;
		padding:20upx 0px 20upx 20upx;
		
		
	}
</style>
