<template>
	<div>
		User
		<div class="btn" @click="add()">
			<h2>用户中心</h2>
			<button>
				发布新闻
			</button>
		</div>
	</div>
</template>

<script>
	export default {
	  name: 'user',
	  methods:{
		 add(){
			 this.$router.push('/Add')
		 } 
	  }
	}
	
</script>

<style scoped lang="stylus">
.btn
	display:flex
	flex-flow:column
	justify-content:space-between
	align-content:space-around
	button
		width:40%
		margin:5%
		padding:3%
		height:50px;
		border-radius:5px;
		border:none
		color:#fff;
		background:#42b983
		font-size:22px
</style>
