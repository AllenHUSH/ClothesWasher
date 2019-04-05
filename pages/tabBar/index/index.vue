<template>
	<view class="content">
		<view>
			<view v-on:click="shangzhuang" class="indexButton">上装</view>
			<view v-on:click="xiazhuang" class="indexButton">下装</view>
			<view v-on:click="xiazhuang" class="indexButton">鞋子</view>
			<view v-on:click="xiazhuang" class="indexButton">其他</view>
        </view>
	</view>
</template>

<script>
	export default {
		data(){
			return{
				Wisher:'wisher'
			}
		},
		methods:{
			shangzhuang(){
				uni.navigateTo({
					url: '../../clothes/blouse/blouse'
				});
			},
			xiazhuang(){
				uni.navigateTo({
					url: '../../clothes/bottom/bottom'
				})
			}
		}
	}
</script>

<style>
.indexButton{
	background-color: #1296db;
	color: #FFFFFF;
	width: 40vw;
	height: 40vw;
	margin: 5vw 5vw;
	float: left;
	line-height: 40vw;
	text-align: center;
}
</style>
