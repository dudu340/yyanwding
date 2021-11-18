<template>
	<view>
		<view class="content">
			<tabs :tabs='tablist' v-on:tabActive='tabActive' />
				<block v-if="contentIndex==0">
					<view class="swiperr">
						<swiper :indicator-dots="true" :autoplay="true" :interval="2000" :duration="1000" circular="true">
							<swiper-item>
								<view class="swiper-item" @tap="previewpic(0)">
									<image class="images" src="../../static/3.png"></image>
								</view>
							</swiper-item>
							<swiper-item>
								<view class="swiper-item" @tap="previewpic(1)">
									
								</view>
							</swiper-item>
						</swiper>
					</view>	
				</block>
				<block v-if="contentIndex==1">
					第二页内容
					<button  size="middle">添加特别关注院校</button  >
				</block>
				<block v-if="contentIndex==2">
					第三页内容
				</block>
			</tabs>
		</view>
	</view>
</template>
<script>
	import tabs from '../../components/Tabs.vue'
	export default {
		data() {
			return {
				tablist: [{
						index: 0,
						value: '已发布',
						isActive: true
					},
					{
						index: 1,
						value: '特别关注',
						isActive: false
					},
					{
						index: 2,
						value: '已删除',
						isActive: false
					}
				],
				contentIndex: '',
				images: []
			}
		},
		methods: {
			tabActive(tabIndex) {
				this.tablist.map((value, index) => {
					value.isActive = tabIndex == index ? true : false
				})
				this.contentIndex = tabIndex
			},
		//轮播图实现图片预览功能
			previewpic(itemsrc){
				uni.previewImage({
					current:itemsrc,
					urls:["../../static/3.png","../../static/4.png"]
				})
			}
		},
		components: {
			tabs,
		}
	}
</script>
<style lang="scss">
	swiper {
		height: 400rpx;
		image {
			width: 100%;
			height: 100vh;
		}
	}
</style>
