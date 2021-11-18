<template>
	<view>
		<view class="content_items">
			<view class="content_item" 
				v-for="(item,index) in tabs" 
				:key="item.index" 
				:class="item.isActive ? 'active' : ''"
				@tap="handlerActive(item.index)"
			>
				{{item.value}}
			</view>
		</view>
		<slot></slot>
	</view>
</template>
<script>
	export default {
		data() {
			return {

			};
		},
		props: {
			tabs: {
				type: Array,
				default: []
			}
		},
		methods:{
			handlerActive(index){
				this.$emit('tabActive',index)
			}
		}
	}
</script>

<style lang="scss">
.content_items {
		display: flex;
		.content_item {
			text-align: center;
			float: left;
			padding: 20px,25px;
			flex: 1;
		}
	}
	.active {
		color: #EB4450;
		border-bottom: 5rpx solid #DD524D;
	}
</style>
