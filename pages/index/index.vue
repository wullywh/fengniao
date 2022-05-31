<template>
	<view>
		<heardNavbar title='首页' iconName='search' rightText="登录|注册" bgColor="#02a774"></heardNavbar>
		</u-navbar>
	</view>
</template>

<script>
	import {
		getCategory
	} from '@/untils/api.js'
	export default {
		data() {
			return {

			}
		},
		onLoad() {
			getCategory()
		},
		methods: {
			rightClick() {
				uni.navigateTo({
					url: "/pages/login/login"
				})
			}
		}
	}
</script>

<style>


</style>
