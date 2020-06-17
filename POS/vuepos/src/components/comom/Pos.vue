<template>
	<div class="pos">
		<el-row>
			<el-col :span='7' class="pos-order" id="order-list">
				<el-tabs>
					<el-tab-pane label="点餐">
						<el-table :data="tableData" border style="width: 100%;">
							<el-table-column prop="goodsName" label="商品名称"></el-table-column>
							<el-table-column prop="count" label="数量"></el-table-column>
							<el-table-column prop="price" label="金额"></el-table-column>
							<el-table-column  label="操作" fixed="right" width="100px">
								<template scope="scope">
									<el-button type="text" size="samll" @click="delmount(scope.row)">删除</el-button>
									<el-button type="text" size="samll"  @click="addOrderList(scope.row)">增加</el-button>
								</template>
							</el-table-column>
						</el-table>
						<div style="margin-top: 10px;">
							<el-button type='warning' @click="HangingList()">挂单</el-button>
							<el-button type='danger' @click="dalallmout()">删除</el-button>
							<el-button type='success' @click="checkout()">结账</el-button>
						</div>
						<div class="Summary">
							<small>数量:</small>{{totalCount}}&nbsp;&nbsp;&nbsp;&nbsp;<small>金额</small>:{{totalMoney}}
						</div>
					</el-tab-pane>
					<el-tab-pane label="挂单">
						<el-table :data="newtableData" border style="width: 100%;">
							<el-table-column prop="goodsName" label="商品名称"></el-table-column>
							<el-table-column prop="count" label="数量"></el-table-column>
							<el-table-column prop="price" label="金额"></el-table-column>
							<el-table-column  label="操作" fixed="right" width="100px">
								<template scope="scope">
									<el-button type="text" size="samll" @click="delmount1(scope.row)">删除</el-button>
									<el-button type="text" size="samll"  @click="addOrderList1(scope.row)">增加</el-button>
								</template>
							</el-table-column>
						</el-table>
						<div style="margin-top: 10px;">
							<el-button type='warning' @click="HangingList()">挂单</el-button>
							<el-button type='danger' @click="dalallmout()">删除</el-button>
							<el-button type='success' @click="checkout()">结账</el-button>
						</div>
						
					</el-tab-pane>
					<el-tab-pane label="外卖">
						外卖
					</el-tab-pane>
				</el-tabs>
			</el-col>
			<el-col :span='17' style="background-color: #f9fcfa;">
					<div class="goods">常用商品</div>
					<div class="goods-food">
						<ul>
							<li v-for="goods in oftenGoods" @click="addOrderList(goods)">
								<span>{{goods.goodsName}}</span>
								<span class="goods-p">￥{{goods.price}}元</span>
							</li>
						</ul>
					</div>
					<div class="goods-type">
						<el-tabs>
						<el-tab-pane label="汉堡">
							<div >
								<ul class="hamburger">
									<li v-for="goods in type3Goods "  @click="addOrderList(goods)">
										<span class="foodimg"><img style="width:50px; height: 50px;" :src="goods.goodsImg" alt=""></span>
										<span class="foodName">{{goods.goodsName}}</span>
										<span class="foodPrice">{{goods.price}}￥</span>
									</li>
								</ul>
							</div>
						</el-tab-pane>
						<el-tab-pane label="小食">
							<div >
								<ul class="hamburger">
									<li v-for="goods in type0Goods "  @click="addOrderList(goods)">
										<span class="foodimg"><img style="width:50px; height: 50px;" :src="goods.goodsImg" alt=""></span>
										<span class="foodName">{{goods.goodsName}}</span>
										<span class="foodPrice">{{goods.price}}￥</span>
									</li>
								</ul>
							</div>
						</el-tab-pane>
						<el-tab-pane label="饮料">
							<div >
								<ul class="hamburger">
									<li v-for="goods in type1Goods "  @click="addOrderList(goods)">
										<span class="foodimg"><img style="width:50px; height: 50px;" :src="goods.goodsImg" alt=""></span>
										<span class="foodName">{{goods.goodsName}}</span>
										<span class="foodPrice">{{goods.price}}￥</span>
									</li>
								</ul>
							</div>
						</el-tab-pane>
						<el-tab-pane label="套餐">
							<div >
								<ul class="hamburger">
									<li v-for="goods in type2Goods " @click="addOrderList(goods)">
										<span class="foodimg"><img style="width:50px; height: 50px;" :src="goods.goodsImg" alt=""></span>
										<span class="foodName">{{goods.goodsName}}</span>
										<span class="foodPrice">{{goods.price}}￥</span>
									</li>
								</ul>
							</div>
						</el-tab-pane>
						</el-tabs>
					</div>
			</el-col>
		</el-row>
	</div>
</template>

<script>
	export default{
		
		name:'pos',
		data(){
			return{
		newtableData:[],
		totalMoney:0,//汇总金额
		totalCount:0,//汇总数量
		tableData:[],
		type0Goods:[
			{
			    goodsId:5,
			    goodsImg:"https://p0.ssl.qhimgs1.com/sdr/400__/t01279438c1ea4e160e.jpg",
			    goodsName:'脆皮炸鸡腿',
			    price:10
			}, {
			    goodsId:6,
			     goodsImg:"https://img.yzcdn.cn/upload_files/2015/04/30/FhEcbA-BNzvwwnY--h8aDa-fCiIj.png!580x580.jpg",
			    goodsName:'魔法鸡块',
			    price:20
			}, 
			{
		              goodsId:9,
		               goodsImg:"https://p1.ssl.qhimgs1.com/sdr/400__/t014c4242e819ea156b.jpg",
		              goodsName:'大块鸡米花',
		              price:15
		          }, {
		              goodsId:20,
		               goodsImg:"https://p0.ssl.qhimgs1.com/sdr/400__/t013679791508e74be6.jpg",
		              goodsName:'香脆鸡柳',
		              price:17
		          },
		],
		type1Goods:[
			{
			    goodsId:7,
			     goodsImg:"https://p5.ssl.qhimgs1.com/sdr/400__/t018a6541711d7621b5.jpg",
			    goodsName:'可乐大杯',
			    price:10
			}, {
			    goodsId:8,
			     goodsImg:"https://p2.ssl.qhimgs1.com/sdr/400__/t018d329e3ae68d700c.jpg",
			    goodsName:'雪顶咖啡',
			    price:18
			}
					
		],
		type2Goods:[
			{
			    goodsId:4,
			    goodsImg:"https://p0.ssl.qhimgs1.com/sdr/400__/t01b8c87b3b371213b4.jpg",
			    goodsName:'快乐全家桶',
			    price:80
			},
		],
		type3Goods:[
		          {
		              goodsId:1,
		              goodsImg:"http://www.8887.tv/upload/201705/08/201705081120261198.jpg",
		              goodsName:'香辣鸡腿堡',
		              price:18
		          }, {
		              goodsId:2,
		              goodsImg:"http://www.hblfoods.com/imageRepository/edd37674-d961-4404-b806-6202a6c6036b.jpg",
		              goodsName:'田园鸡腿堡',
		              price:15
		          }, {
		              goodsId:3,
		              goodsImg:"https://p0.ssl.qhimgs1.com/sdr/400__/t01b28bdee7aa55595e.jpg",
		              goodsName:'和风汉堡',
		              price:15
		          }, 
		      ],
	   oftenGoods:[
		          {
		              goodsId:1,
		              goodsName:'香辣鸡腿堡',
		              price:18
		          }, {
		              goodsId:2,
		              goodsName:'田园鸡腿堡',
		              price:15
		          }, {
		              goodsId:3,
		              goodsName:'和风汉堡',
		              price:15
		          }, {
		              goodsId:4,
		              goodsName:'快乐全家桶',
		              price:80
		          }, {
		              goodsId:5,
		              goodsName:'脆皮炸鸡腿',
		              price:10
		          }, {
		              goodsId:6,
		              goodsName:'魔法鸡块',
		              price:20
		          }, {
		              goodsId:7,
		              goodsName:'可乐大杯',
		              price:10
		          }, {
		              goodsId:8,
		              goodsName:'雪顶咖啡',
		              price:18
		          }, {
		              goodsId:9,
		              goodsName:'大块鸡米花',
		              price:15
		          }, {
		              goodsId:20,
		              goodsName:'香脆鸡柳',
		              price:17
		          }
		
		      ]
			}
		},
		mounted:function(){
			var orderHeiht=document.body.clientHeight;
			document.getElementById('order-list').style.height=orderHeiht+'px';
		},
		methods:{
			addOrderList(goods){
				this.totalCount=0;
				this.totalMoney=0;
				let isHave = false;
				for(let i=0;i<this.tableData.length;i++){
					console.log(this.tableData[i].goodsId)
					if(this.tableData[i].goodsId==goods.goodsId){
						isHave = true;
					}	
					}
					if(isHave){
						let arr = this.tableData.filter(o => o.goodsId == goods.goodsId)
						arr[0].count++;
					}else{
						let NewGoods={goodsId:goods.goodsId,goodsName:goods.goodsName,price:goods.price,count:1}
						this.tableData.push(NewGoods)
					}
					this.getAllMoney();
			},
			delmount(goods){
				this.tableData=this.tableData.filter(o => o.goodsId != goods.goodsId);
				this.getAllMoney();
			},
			delmount1(goods){
				this.newtableData=this.newtableData.filter(o => o.goodsId != goods.goodsId);
				this.getAllMoney();
			},
			getAllMoney(){
			    this.totalCount=0;
			    this.totalMoney=0;
			    if(this.tableData){
			           this.tableData.forEach((element) => {
			        this.totalCount+=element.count;
			        this.totalMoney=this.totalMoney+(element.price*element.count);   
			    });
			    }
			
			},
			dalallmout(){
				this.tableData=[];
				this.totalCount=0;
				this.totalMoney=0;
			},
			checkout() {
				if(this.totalCount!=0){
					this.tableData=[];
					this.totalCount=0;
					this.totalMoney=0;
					this.$message({
					            message: '结账成功，感谢你又为店里出了一份力!',
					            type: 'success'
					        });
				}else{
					this.$message.error('不能空结。老板了解你急切的心情！');
				}
				
			},
			HangingList(){
				console.log(this.tableData)
				for(let i=0;i<this.tableData.length;i++){
					this.newtableData.push(this.tableData[i])
				}
				this.tableData=[];
				this.totalCount=0;
				this.totalMoney=0;
			},
		
			
		}
	}
</script>

<style>
	.Summary{
		margin-top: 20px;
	}
	   .foodName{
	       font-size: 18px;
	       padding-left: 10px;
	       color:brown;
	
	   }
	   .foodPrice{
	       font-size: 16px;
	       padding-left:35px;
	       padding-top:15px;
	   }
	.hamburger li span{
		display: block;
		float: left;
	}
	.hamburger li{
		list-style: none;
		margin: 10px;
		padding: 2px;
		float: left;
		background-color: #FFFFFF;
		border: 1px solid #e5e9ef;
		height: auto;
		width: 23%;
	}
	.foodimg{
		width: 40%;
	}
	.goods-p{
		color: #58B7FF;
	}
	.goods-food ul li{
		height: 20px;
		float: left;
		list-style: none;
		border: 1px solid #D3DCE6;
		background-color: #FFFFFF;
		padding: 10px;
		margin: 15px;
	}
	.goods{
		padding: 10px;
		background-color: #f9fcfa;
		font-size: 15px;
		line-height: 20px;
		text-align: left;
		height:20px;
		border-bottom: 1px solid #D3DCE6;
	}
	.pos{
		text-align: center;
	}
	.pos-order{
		background-color: #f9fafc;
		border-right: 1px solid #C0CCDA;
	}
	.goods-type{
		padding: 0;
		text-align: center;
		clear: both;
	}
	.el-tabs{
		padding: none;
	}
	.el-tabs--top .el-tabs__item.is-top:nth-child(2){
		padding-left: 10px !important;
	}

</style>
