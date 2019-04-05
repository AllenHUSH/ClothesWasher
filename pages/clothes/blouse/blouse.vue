<template>
	<view>
		<text>上装</text>
		<view v-for="clothesInfo">
			<image src="../../../static/img/1.jpg"></image>
			<view>
				<text v-text=""></text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				clothesInfo:[
					{
						imgSrc: '../../../static/img/'+1+'.jpg',
						name:'',
						price: ''
					}
				]
			};
		}
	}
</script>

<style>

</style>
