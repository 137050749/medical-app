<template>
	<view>
		<view class="header">
			<image class="logo" src="/static/images/logo.png"></image>
		</view>
		<view class="title" v-if="list.length>0">
			{{list[index].title}}
		</view>
		<image class="img-detail" v-if="list.length>0" :src="list[index].imgurl" mode=""></image>
		<template  v-if="list.length>0 && list[index] && list[index].content" >
			<view class="content" v-for="(item,id) in list[index].content" :key="id">
				<view v-html="item.first_line"></view>
				<view v-html="item.second_line"></view>
			</view>
		</template>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				index:-1,
				list: [],
				// currData: null
			}
		},
		onLoad(option) {
			this.index = option.newsId
				uni.request({
					url: '../../static/data/news.json',
					method: 'GET',
					data: {},
					success: (res) => {
						this.list = res.data.data
						// this.currData = this.list[this.index].content
					},
					fail: (err) => { console.log(err)},
					complete: () => {}
				})			
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
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
	.title{
		font-size: 32upx;
		font-weight: 800;
		text-align: center;
		padding: 20upx;
		// margin-top:70upx;
	}
	.img-detail{
		width: 90%;
		margin-left: 5%;
	}
	.content{
		padding: 18upx;
		font-size: 28upx;
		line-height: 40upx;
	}
</style>
