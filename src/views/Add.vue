<template>
	<div class="add">
		<h2>新闻标题</h2>
		<input type="text" v-model="title" />
		<h2>内容</h2>
		<textarea type="text" v-model="content" class="content" />
		<div class="btn" @click="add()"><button>确认发布</button></div>
	</div>
</template>

<script>
import store from '../store.js';
export default {
	name: 'Add',
	data() {
		return {
			title: '',
			content: ''
		};
	},
	methods: {
		add() {
			store.commit('addItem', {
				title:this.title,
				content: this.content
			});
			this.title = '';
			this.content = '';
			this.$router.push('/home/list');
		}
	}
};
</script>

<style scoped lang="stylus">
input
		border:1px solid black
		height:30px
		font-weight:bolder
		font-size:22px
.content
		border:1px solid black
		font-size:20px
		height:400px
.add
	width:90%
	margin:5%
	display:flex
	flex-flow:column
	align-content:space-between
	h2
		display:flex		
		font-weight:500
		color:#42b983
.btn
		display:flex
		flex-flow:row no-wrap
		justify-content:flex-end
		button
			margin:5%
			padding:3%
			border:none
			
			height:50px;
			border-radius:5px;
			border:none;
			color:#fff;
			background:#42b983
			font-size:22px
</style>
