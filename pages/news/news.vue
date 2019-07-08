<template>
	<view class="news">
		<view class="header">
			<image class="logo" src="/static/images/logo.png"></image>
		</view>
		<view class="content">
			<view class="uni-list">
				<view class="uni-list-cell" @tap="todetail" :data-newsid="item.id" hover-class="uni-list-cell-hover" v-for="item in newslist.data" :key="item.id">
					<view class="uni-media-list"  >
						<view class="image-view">
							<image class="item-img" :src="item.imgurl"></image>
						</view>
						<view class="uni-media-list-body">
							<view class="uni-media-list-text-top">{{item.title}}</view>
							<view class="uni-media-list-text-bottom uni-ellipsis">{{item.time}}</view>
						</view>
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
				newslist: []
			};
		},
		onLoad() {
			uni.showLoading({
				title: '新闻',
				mask: false
			});
			uni.request({
				url: '../../static/data/news.json',
				method: 'GET',
				data: {},
				success: res => {
					this.newslist = res.data
					uni.hideLoading()
				},
				fail: (err) => {console.log(err)},
				complete: () => {}
			});
		},
		methods: {
			todetail(e) {
				let newsid = e.currentTarget.dataset.newsid
				uni.navigateTo({
					url: '../detail/detail?newsId=' + newsid
				})
			}
		}
	}
</script>

<style lang="scss">
	.news{
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
		.content{
			.uni-list{
				.uni-list-cell{
					.uni-media-list{
						display: flex;
						.image-view{
							.item-img{
								width: 200upx;
								height: 120upx;
								margin: 20upx 20upx 0 20upx;
								overflow: hidden;
							}
						}
						.uni-media-list-body{
							.uni-media-list-text-top{
								font-size: 28upx;
								margin-top: 20upx;
								color: #666666;
							}
							.uni-media-list-text-bottom{
								font-size: 24upx;
								color: #CCCCCC;
								margin-top: 10upx;
							}
						}
					}
				}
			}
		}
	}
	
</style>
