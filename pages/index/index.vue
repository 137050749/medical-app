<template>
	<view class="contentwrapper">
		<view class="header">
			<image class="logo" src="/static/images/logo.png"></image>
		</view>
		<view class="uni-padding-wrap">
		    <view class="page-section swiper">
		        <view class="page-section-spacing">
		            <swiper circular="true" class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
		                <swiper-item>
		                    <view class="swiper-item">
								<image class="banner-img" src="http://protal.mdmooc.org/v2/portal/images/pjhl.jpg" mode=""></image>
							</view>
		                </swiper-item>
		                <swiper-item>
		                    <view class="swiper-item">
								<image class="banner-img" src="http://protal.mdmooc.org/v2/portal/images/xlztcbanner.png" mode=""></image>
							</view>
		                </swiper-item>
		                <swiper-item>
		                    <view class="swiper-item">
								<image class="banner-img" src="http://protal.mdmooc.org/app/images/wamapc.png" mode=""></image>
							</view>
		                </swiper-item>
						<swiper-item>
						    <view class="swiper-item">
								<image class="banner-img" src="http://protal.mdmooc.org/v2/portal/images/banner_index2.jpg" mode=""></image>
							</view>
						</swiper-item>
						<swiper-item>
						    <view class="swiper-item">
								<image class="banner-img" src="http://protal.mdmooc.org/v2/portal/images/cmebanner.jpg" mode=""></image>
							</view>
						</swiper-item>
		            </swiper>
		        </view>
			</view>
		</view>
		<view class="choose-list">
			<view class="list-top">
				<view class="list-item" @tap="toItemDetail">实践提升</view>
				<view class="list-item" @tap="toItemDetail">职业发展</view>
				<view class="list-item" @tap="toItemDetail">学术课件</view>
				<view class="list-item" @tap="toItemDetail">医学学说</view>
			</view>
			<view class="list-bottom">
				<view class="list-item" @tap="toItemDetail">公开课堂</view>
				<view class="list-item" @tap="toItemDetail">实践社群</view>
				<view class="list-item" @tap="toItemDetail">临床技能</view>
				<view class="list-item" @tap="toItemDetail">上传课件</view>
			</view>
		</view>
		<view class="content">
			<view class="course-item">
				<view class="title">精品课程 ></view>
				<hr>
				<view class="boutique">
					<scroll-view class="scroll-view_H" scroll-x="true" @scroll="scroll" scroll-left="0">
						<view class="course-info scroll-view-item_H">
							<image class="course-img" src="http://www.mdmooc.org/media/temp/v3/dati.jpg" mode=""></image>
							<view class="course-name">注射用质子泵抑制剂临床应用全领域医观点调研</view>
						</view>
						<view class="course-info scroll-view-item_H">
							<image class="course-img" src="http://file.mdmooc.com/meddata/ccmedpfile/crs_vid_imgs/2019/06/11/79371618205746509064829cfc0bb4b1.jpg" mode=""></image>
							<view class="course-name">皮菌话聊——基层皮肤感染规范诊治课程</view>
						</view>
						<view class="course-info scroll-view-item_H">
							<image class="course-img" src="http://file.mdmooc.com/meddata/ccmedpfile/crs_vid_imgs/2019/02/26/20e507a94a184d3ca486a4acb661bd8a.png" mode=""></image>
							<view class="course-name">中国关节炎与疼痛管理</view>
						</view>
					</scroll-view>
				</view>
			</view>
			<view class="course-item">
				<view class="title">TED专区 ></view>
				<hr>
				<view class="boutique">	
					<scroll-view class="scroll-view_H" scroll-x="true" @scroll="scroll" scroll-left="0">
						<view class="course-info scroll-view-item_H">
							<image class="course-img" src="http://file.mdmooc.com/meddata/ccmedpfile/crs_vid_imgs/2019/04/12/f4033a8955f347cabfd3259e3276b5e8.jpg" mode=""></image>
							<view class="course-name">儿童患者：必须更谨慎地选择抗菌药物</view>
						</view>
						<view class="course-info scroll-view-item_H">
							<image class="course-img" src="http://file.mdmooc.com/meddata/ccmedpfile/crs_vid_imgs/2019/04/12/9765d46b97ef407da7200976389ec3a6.jpg" mode=""></image>
							<view class="course-name">如何进行急诊经验性抗感染治疗</view>
						</view>
						<view class="course-info scroll-view-item_H">
							<image class="course-img" src="http://file.mdmooc.com/meddata/ccmedpfile/crs_vid_imgs/2019/04/12/3d135160a2ca4e12bbe113f643aaad9e.jpg" mode=""></image>
							<view class="course-name">抗感染的临床实践——病例分享之鼻窦炎</view>
						</view>
					</scroll-view>
				</view>
			</view>
			<view class="course-item">
				<view class="title">名家访谈 ></view>
				<hr>
				<view class="boutique">	
					<scroll-view class="scroll-view_H" scroll-x="true" @scroll="scroll" scroll-left="0">
						<view class="course-info scroll-view-item_H">
							<image class="course-img" src="http://file.mdmooc.com/meddata/ccmedpfile/crs_vid_imgs/2019/05/10/f3a845d8fcec49118388274ab0a9887a.jpg" mode=""></image>
							<view class="course-name">ECCMID 2019中欧直播连线课程</view>
						</view>
						<view class="course-info scroll-view-item_H">
							<image class="course-img" src="http://file.mdmooc.com/meddata/ccmedpfile/crs_vid_imgs/2018/11/26/9052baeb976b4650af8adec335783806.jpeg" mode=""></image>
							<view class="course-name">士代阳光|中国心身教育联盟抑郁讲堂</view>
						</view>
						<view class="course-info scroll-view-item_H">
							<image class="course-img" src="http://file.mdmooc.com/meddata/ccmedpfile/crs_vid_imgs/2019/02/27/67dc9494b1f14f97bc0d7cf333a3a899.png" mode=""></image>
							<view class="course-name">“痫”聊直通车线上学术中心</view>
						</view>
					</scroll-view>
				</view>
			</view>
		</view>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				duration: 500.,
				scrollTop: 0,
				old: {
					scrollTop: 0
				}
			}
		},
		onLoad() {

		},
		methods: {
			changeIndicatorDots(e) {
				this.indicatorDots = !this.indicatorDots
			},
			changeAutoplay(e) {
				this.autoplay = !this.autoplay
			},
			intervalChange(e) {
				this.interval = e.target.value
			},
			durationChange(e) {
				this.duration = e.target.value
			},
			scroll(e) {
				this.old.scrollTop = e.detail.scrollTop
			},
			toItemDetail(){
				uni.navigateTo({
					url: '../item-detail/item-detail'
				})
			}
		}
	}
</script>

<style lang="scss">
	.contentwrapper {
		text-align: center;
		padding-bottom: 40upx;
		.header{
			.title {
				font-size: 36upx;
				color: #8f8f94;
			}
			.logo{
				width: 160upx;
				height: 50upx;
				position: fixed;
				top: 20upx;
				left: 20upx;
				z-index: 1000;
			}
		}
		.uni-padding-wrap{
			padding: 0;
			.page-section{
				.page-section-spacing{
					.swiper{
						.swiper-item{
							width: 750upx;
							height: 300upx;
							.banner-img{
								width: 100%;
								overflow: hidden;
								height: 100%;
							}
						}
					}
				}
			}
		}
		.choose-list{
			.list-top,.list-bottom{
				display: flex;
				font-size: 28upx;
				justify-content: space-around;
				margin: 40upx 0px;
				color: #8f8f94;
				.list-item{
					border: 1px solid #ccc;
					padding: 14upx;
					border-radius: 8upx;
				}
			}
		}
		.content{
			.course-item{
				.title{
					font-size: 32upx;
					color: #8f8f94;
					padding: 20upx;
					text-align: left;
				}
				.boutique{
					display: flex;
					box-shadow: 1px 1px 4px #ccc;
					.scroll-view_H{
						box-sizing: border-box;
						width: 100%;
						white-space: nowrap;
						.scroll-view-item_H {
							display: inline-block;
							width: 100%;
							height: 300upx;
							text-align: center;
							font-size: 36upx;
						}
						.course-info{
							width: 300upx;
							padding:20upx 0px 20upx 20upx;
							.course-img{
								width: 100%;
								height: 180upx;
							}
							.course-name{
								width: 100%;
								font-size: 24upx;
								white-space: nowrap;
								overflow: hidden;
								text-overflow: ellipsis;
							}
						}
					}
				}
			}
		}
	}
	
</style>
