<template>
	<div>
		<h1 class="header">欢迎登陆</h1>
		<form action="" v-if="!isReg" class="log_reg">
			<div class="section">
				<label>用户名:</label>
				<input type="text" v-model="name" />
			</div>
			<div class="section">
				<label>密码：</label>
				<input type="password" v-model="password" />
			</div>
			
			<div class="btn">
				<button type="button" @click="log()">登录</button>
				<button type="button" @click="reg()">注册</button>
			</div>
		</form>
		<form action="" v-else class="log_reg">
			<div class="section">
				<label>用户名:</label>
				<input type="text" v-model="name" />
			</div>
			<div class="section">
				<label>密码：</label>
				<input type="password" v-model="password" />
			</div>

			
			<div class="section">
				<label>确认密码：</label>
				<input type="password" v-model="repeat" />
			</div>
			
			<div class="btn">
				<button type="button" @click="addUser()">确定</button>
				<button type="button" @click="cancel()">取消</button>
			</div>
		</form>
	</div>
</template>

<script>
export default {
	name: 'Login',
	data() {
		return {
			isReg: false,
			name: '',
			password: '',
			repeat: ''
		};
	},
	methods: {
		log() {
			if(localStorage.getItem("name")===this.name && localStorage.getItem("password")===this.password){
				this.$router.push('/home/list')
				this.name=''
				this.password=''
			}else{
				alert('用户名密码不正确')
			}
			
		},
		reg() {
			this.isReg = true;
		},
		addUser() {
			if (this.password == this.repeat) {
				localStorage.setItem('name', this.name);
				localStorage.setItem('password', this.password)
				this.name=''
				this.password=''
				this.repeat=''
				this.isReg=false
			} else {
				alert('两次密码不一致！');
			}
		},
		cancel() {
			this.isReg = false;
		}
	}
};
</script>

<style scoped lang="stylus">
	.header
		display: block;
		position: absolute;
		top: 20%;
		left: 15%;
	.log_reg
		position: absolute;
		width: 80%;
		display: flex;
		flex-direction: column;
		width: 80%;
		top: 30%;
		left:10%
		
		label
			font-size: 22px;
			color:#42b983;
	.section	
		display:flex;
		margin:3%
		flex-direction:row;
		justify-content:space-between;
		align-items:center
		input
			line-height:25px
			border:1px solid black;
			
	.btn  
		display:flex;
		flex-flow:row nowrap
		justify-content:space-around;
		align-items:center
		margin-top:20%
		:last-child
			background:#fff
			color:#2a2a2a
			border:1px solid #eaeaea
		button
			width:30%
			height:50px;
			border-radius:5px;
			border:none;
			color:#fff;
			background:#42b983
			font-size:25px
			
</style>
