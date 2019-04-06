<template>
	<view>
		<view class="basketBox" v-for="(item,index) in goodInfo">
			<image v-bind:src="item.imgSrc" mode="widthFix"></image>
			<view id="infoBox">
				<text v-text="item.name">商品名称</text>
				<text v-text="'单价：¥'+item.price"></text>
				<input type="number" min="1" v-model="item.amount"/>
				<button v-on:click="addAmount" v-bind:data-num="index">+</button>
				<button v-on:click="subAmount" v-bind:data-num="index">-</button>
			</view>
		</view>
		<view v-if="!goodInfo.length" id="none">
			<text>洗衣篮中什么都没有呢</text>
			<text>快去添加吧</text>
		</view>
		<view id="payBox">
			<text>合计：{{tatal}}</text>
		</view>
	</view>
</template>

<script>
	// 引入公共的bug，来做为中间传达的工具
	import Bus from '../../../components/bus.js'
	export default {
		data() {
			return {
				tatal:0.00,
				goodInfo:[
					//等待接受数据
// 					{
// 					amount: 1,
// 					img: "blouse",
// 					imgSrc: "../../../static/img/blouse/1.jpg",
// 					name: "羽绒服",
// 					num: 0,
// 					price: "49.9",
// 					}
				]
			};
		},
		onLoad() {
			this.tatalPay();
			console.log("hi");
			console.log(this.goodInfo.length);
		},
		mounted: function () {
			var that = this
			// 用$on事件来接收参数
			Bus.$on('val', (tempData) => {
				tempData.amount = 1;
				tempData.imgSrc = "../../../static/img/"+tempData.img+"/"+(tempData.num+1)+".jpg";
				console.log(tempData);
				that.goodInfo.push(tempData);
				this.tatalPay();
			})
        },
		methods:{
			tatalPay(){
				console.log(this.goodInfo.length);
				this.tatal = 0.00;
				for(var i=0;i<this.goodInfo.length;i++){
					// this.tatal = parseInt(this.goodInfo[i].price) * parseInt(this.goodInfo[i].amount);
					this.tatal = parseFloat(this.goodInfo[i].price) * parseFloat(this.goodInfo[i].amount) + this.tatal;
					// this.tatal = this.goodInfo[i].price * this.goodInfo[i].amount;
					// this.tatal = eval(this.goodInfo[i].price * this.goodInfo[i].amount);
				}
			},
			addAmount(ev){
				var num = ev.target.dataset.num;
				this.goodInfo[num].amount++;
				this.tatalPay();
			},
			subAmount(ev){
				var num = ev.target.dataset.num;
				this.goodInfo[num].amount--;
				this.tatalPay();
			}
		}
	}
</script>

<style>
.basketBox{
	background-color: #1296DB;
	color: #FFFFFF;
	width: 90vw;
	margin: 10px 5vw;
	border-radius: 3vw;
}
.basketBox image{
	width: 30vw;
	float: left;
}
#infoBox{
	width: 60vw;
}
.basketBox text{
	display: block;
}
.basketBox button{
	width: 10vw;
	display: inline-block;
}
.basketBox input{
	width: 30vw;
	display: inline-block;
}
#none text{
	margin: 50px 0;
	font-size: 30px;
	display: block;
	color: #DDDDDD;
	text-align: center;
}
#payBox{
	position: fixed;
}
</style>
