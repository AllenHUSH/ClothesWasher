<template>
	<view class="mainBox">
		<view v-for="(item,index) in clothesInfo" class="goodBox">
			<image v-bind:src="item.imgSrc+'bottom/'+(index+1)+'.jpg'" mode="widthFix"></image>
			<view>
				<text v-text="item.name">商品名称</text>
				<text v-text="item.price">价格</text>
				<button>加入洗衣篮</button>
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
						imgSrc: '../../../static/img/',
						name:'牛仔裤',
						price: '¥19.9'
					},
					{
						imgSrc: '../../../static/img/',
						name:'半身裙',
						price: '¥19.9'
					},
					{
						imgSrc: '../../../static/img/',
						name:'西服裤子',
						price: '¥29.9'
					},
					{
						imgSrc: '../../../static/img/',
						name:'保暖裤',
						price: '¥29.9'
					},
					{
						imgSrc: '../../../static/img/',
						name:'休闲裤/运动裤',
						price: '¥29.9'
					},
					{
						imgSrc: '../../../static/img/',
						name:'连衣裙',
						price: '¥49.9'
					},
					{
						imgSrc: '../../../static/img/',
						name:'连体裤',
						price: '¥39.9'
					},
					{
						imgSrc: '../../../static/img/',
						name:'毛裤',
						price: '¥29.9'
					}
				]
			};
		}
	}
</script>

<style>
.mainBox{
	-moz-column-count:2; /* Firefox */
    -webkit-column-count:2; /* Safari 和 Chrome */
    column-count:2;
    width: 100%;
}
.goodBox{
	background-color: #1296DB;
	width: 40vw;
	margin: 20px 4.5vw;
	float: left;
	border: #1296DB 1px solid;
	color: #FFFFFF;
	text-align: center;
	border-radius: 3vw;
	padding: 3vw 0 3vw;
    -moz-page-break-inside: avoid;
    -webkit-column-break-inside: avoid;
    break-inside: avoid;
}
.goodBox text{
	display: block;
	width: 100%;
}
.goodBox image{
	width: 100%;
}
.goodBox button{
	color: #1296DB;
	border-radius: 3vw;
}
</style>
