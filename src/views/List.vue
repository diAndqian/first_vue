<template>
	<div>
		<div>List</div>
		<ul class="list">
			<li v-for="(item, index) in pagelists" :key="index">
				<h2>{{item.title}}</h2>
				<textarea v-model="item.content">
			    </textarea>
			</li>
		</ul>
	</div>
</template>

<script>
import store from '../store.js';
export default {
	name: 'list',
	store,
	computed: {
		pagelists() {
			return store.state.lists;
		}
	}
};
</script>

<style scoped lang="stylus">
	.list
		list-style-type: none;
		width: 90%;
		margin: 5%;
		display: flex;
		flex-direction: column;
		justify-content:space-around
		h2
			color:#42b983
			margin: 5%;
		textarea
			width: 100%
			height: 100px;
			border:1px solid #42b983
			font-size: 20px;
			
</style>
