<template>
	<view class="content">
		<view>
            <text class="title">{{Wisher}}</text>
			<button v-on:click="shangzhuang">上装</button>
			<button v-on:click="xiazhuang">下装</button>
			<button>鞋子</button>
			<button>其他</button>
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
				this.$data.Wisher = 'Hi';
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
	
</style>
