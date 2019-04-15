<template>
	<view>
		<view class="basketBox" v-for="(item,index) in goodInfo">
			<image v-bind:src="item.imgSrc" mode="widthFix"></image>
			<view id="infoBox">
				<text v-text="item.name" style="font-size: 8vw;">商品名称</text>
				<text v-text="'单价：¥'+item.price"></text>
				<button v-on:click="addAmount" v-bind:data-num="index">+</button>
				<input type="number" v-model="item.amount"/>
				<button v-on:click="subAmount" v-bind:data-num="index">-</button>
			</view>
		</view>
		<view v-if="!goodInfo.length" id="none">
			<text>洗衣篮中什么都没有呢</text>
			<text>快去添加吧</text>
		</view>
		<view id="payBox">
			<text>合计：¥{{tatal}}</text>
			<button v-on:click="pay">付款</button>
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
			let that = this
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
				for(let i=0;i<this.goodInfo.length;i++){
					let temp = parseFloat(this.goodInfo[i].price) * parseFloat(this.goodInfo[i].amount) + this.tatal;
					this.tatal = temp;
				}
			},
			addAmount(ev){
				let num = ev.target.dataset.num;
				this.goodInfo[num].amount++;
				this.tatalPay();
			},
			subAmount(ev){
				let num = ev.target.dataset.num;
				this.goodInfo[num].amount--;
				if(this.goodInfo[num].amount<1)this.goodInfo[num].amount=1;
				this.tatalPay();
			},
			pay(){
				location.reload()
			}
		}
	}
</script>

<style>
.basketBox{
	background-color: #1296DB;
	color: #FFFFFF;
	width: 90vw;
	margin: 10px 5vw 10px 2vw;
	border-radius: 3vw;
	padding: 3vw;
}
.basketBox image{
	width: 30vw;
	display: inline-block;
}
#infoBox{
	width: 60vw;	
	display: inline-block;
}
.basketBox text{
	display: block;
}
.basketBox button{
	width: 10vw;
	height: 10vw;
	display: inline-block;
}
.basketBox input{
	background-color: #FFFFFF;
	height: 10vw;
	line-height: 10vw;
	width: 10vw;
	text-align: center;
	display: inline-block;
	color: #000000;
}
#none text{
	margin: 50px 0;
	font-size: 30px;
	display: block;
	color: #DDDDDD;
	text-align: center;
}
#payBox{
	text-align: center;
	background-color: #1296DB;
	color: #FFFFFF;
}
</style>
