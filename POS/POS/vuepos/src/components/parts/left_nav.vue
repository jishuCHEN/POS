<template>
	<div class="left_nav">
		<ul>
			<li>
				<i class="icon iconfont icon-searchcart"></i>
				<div class="">收银</div>
			</li>
			<li>
				<i class="icon iconfont icon-store "></i>
				<div class="">商铺</div>
			</li>
			<li>
				<i class="icon iconfont icon-hanbao "></i>
				<div class="">商品</div>
			</li>
			<li>
				<i class="icon iconfont icon-office-supplies "></i>
				<div class="">会员</div>
			</li>
			<li>
				<i class="icon iconfont icon-conditions "></i>
				<div class="">设置</div>
			</li>
		</ul>
	</div>
</template>

<script>
	export default{
		
	}
</script>
<style>
	*{
		margin: 0;
		padding: 0;
	}
	.left_nav{
		float: left;
		background-color: #1d8ce0;
		height: 100%;
		font-size: 10px;
		color: #fff;
		width: 5%;
	}
	.iconfont{
		font-size: 24px;
	}
	.left_nav li{
		border-bottom: 1px solid #fff;
		text-align: center;
		list-style:none;
		padding: 10px;
	}
	.left_nav ul{
		height: 100%;
	}
</style>
