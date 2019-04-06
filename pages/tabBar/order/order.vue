<template>
	<view>
		<view id="userBox">
			<image v-bind:src="'../../../static/userInfo/'+userInfo.chatHead+'.png'" mode="widthFix"></image>
			<text v-text="'Hi,'+userInfo.name"></text>
		</view>
		<view class="itemBox">
			<text class="itemText">已付款</text>
			<text class="itemText">待付款</text>
			<text class="itemText">待上门取货</text>
		</view>
		<view class="itemBox">
			<text class="itemText">我的地址</text>
			<text class="itemText">联系商家</text>
			<text class="itemText">设置</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userInfo:{
					chatHead:'head',
					name:'TestName'
				}
			};
		}
	}
</script>

<style>
#userBox{
	margin: 20px 0;
	width: 100vw;
	align-items: center;
	text-align: center;
}
#userBox image{
	width: 30%;
	display: block;
	margin: 0 auto;
}
.itemBox{
	width: 90vw;
	margin: 10px 5vw;
}
.itemText{
	width: 28vw;
	height: 28vw;
	display: inline-block;
	line-height: 26vw;
	background-color: #1296DB;
	color: #FFFFFF;
	margin: 0 1vw;
	text-align: center;
}
</style>
