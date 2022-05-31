<template>
	<view>
		<heardNavbar iconColor="#606266"></heardNavbar>
		<view class="a">
			登录页面
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			rightClick() {
				console.log(111)
				uni.navigateTo({
					url: "/pages/index/index"
				})
			}
		}
	}
</script>

<style>
	.header-nav {
		background-color: white;
	}
</style>
