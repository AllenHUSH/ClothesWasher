<template>
	<view class="mainBox">
		<view v-for="(item,index) in clothesInfo" class="goodBox">
			<image v-bind:src="item.imgSrc+'other/'+(index+1)+'.jpg'" mode="widthFix"></image>
			<view>
				<text v-text="item.name">商品名称</text>
				<text v-text="'¥'+item.price">价格</text>
				<button v-on:click="addTobasket" v-bind:data-num="index" data-img="other">加入洗衣篮</button>
			</view>
		</view>
	</view>
</template>

<script>
	// 引入公共的bug，来做为中间传达的工具
	import Bus from '../../../components/bus.js'
	export default {
		data() {
			return {
				clothesInfo:[
					{
						imgSrc: '../../../static/img/',
						name:'皮包（小）',
						price: '39.9'
					},
					{
						imgSrc: '../../../static/img/',
						name:'皮包（大）',
						price: '59.9'
					},
					{
						imgSrc: '../../../static/img/',
						name:'书包',
						price: '19.9'
					},
					{
						imgSrc: '../../../static/img/',
						name:'帽子',
						price: '19.9'
					},
					{
						imgSrc: '../../../static/img/',
						name:'丝巾',
						price: '29.9'
					},
					{
						imgSrc: '../../../static/img/',
						name:'围巾',
						price: '29.9'
					}
				]
			};
		},
		methods:{
			addTobasket: function (ev) {
				var num = ev.target.dataset.num;
				var img = ev.target.dataset.img;
				var json = [];
				var busData = {};
				busData.name = this.$data.clothesInfo[num].name;
				busData.price = this.$data.clothesInfo[num].price;
				busData.img = img;
				busData.num = parseInt(num);
				console.log(busData);
				Bus.$emit('val',busData);
			}
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
