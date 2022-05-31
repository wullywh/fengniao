<template>
	<view class="header-nav">
		<view class="left">
			<u-icon :name="iconName_l" size="19" :color="iconColor"></u-icon>
			<text>{{leftText}}</text>
		</view>
		<view class="title">
			{{title}}
		</view>
		<view class="right">
			{{rightText}}
			<u-icon :name="iconName_r" size="19"></u-icon>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			leftText: {
				type: String,
				default: ''
			},
			rightText: {
				type: String,
				default: ''
			},
			title: {
				type: String,
				default: ''
			},
			iconColor: {
				type: String,
				default: 'white'
			},
			iconName_l: {
				type: String,
				default: 'arrow-left'
			},
			iconName_r: {
				type: String,
				default: ''
			}
		},
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style lang="scss">
	.header-nav {
		width: 100%;
		align-items: center;
		justify-content: space-evenly;
		display: flex;
		height: 88rpx;
		color: white;
		background-color: #02a774;

		.left {
			width: 20%;
			padding-left: 30rpx;
			display: flex;
			align-items: center;
			height: 100%;
			text-align: left;
			font-size: 28rpx;

		}

		.right {
			width: 20%;
			padding-right: 30rpx;
			line-height: 88rpx;
			height: 100%;
			text-align: right;
			font-size: 28rpx;

		}

		.title {
			width: 60%;
			height: 100%;
			line-height: 88rpx;
			text-align: center;
			font-size: 36rpx;
			flex-grow: 1;
		}
	}
</style>
