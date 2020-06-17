<template>
  <div id="app">
	 <leftNav></leftNav>
	 <div class="mian"> 
	 <router-view></router-view>
     </div>
   
  </div>
</template>
<script>
	import leftNav from '@/components/parts/left_nav.vue'
	export default{
		name:'app',
		components:{
			leftNav
		}
	}
</script>
<style>
	.mian{
		float: left;
		width: 95%;
	}
</style>
