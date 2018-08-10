<template>
	<div class='tab' @mouseover='stop' @mouseleave='play'>
		<ul class='top'>
			<li v-for='(v,i) in imgs' :style='{backgroundImage:"url("+v+")",backgroundSize:"cover"}' v-show='i===index?true:false'></li>
		</ul>
		<ol class='circle' :style='{width:imgs.length*20+"px",height:"20px"}'>
			<li v-for='(v,i) in imgs' :class='i==index?"active":""'></li>
		</ol>
		<ul class='bottom' :style='{width:imgs.length*80+"px",height:"100px"}'>
			<li v-for='(v,i) in imgs' :style='{backgroundImage:"url("+v+")",backgroundSize:"cover"}' @click='change(i)'></li>
		</ul>
	</div>
</template>
<script>
	export default{
		props:['tab'],
		data(){
			return {
				imgs:[],
				index:0,
				timer:null
			}
		},
		created(){
			this.imgs = this.tab.imgs;
			this.index = this.tab.index;	
			this.timer = this.tab.timer;
		},
		mounted(){
			clearInterval(this.timer);
			this.timer = setInterval(function(){
				this.index++;
			   if(this.index===this.imgs.length){
			   	 this.index = 0;
			   }
			}.bind(this),1000)
		},
		methods:{
			change(i){
				this.index = i;
			},
			stop(){
				clearInterval(this.timer);
				var bot = document.querySelector('.bottom');
				bot.style.bottom = '7px';
			},
			play(){
				clearInterval(this.timer);
				this.timer = setInterval(function(){
					this.index++;
				   if(this.index===this.imgs.length){
				   	 this.index = 0;
				   }
				}.bind(this),1000);
				var bot = document.querySelector('.bottom');
				bot.style.bottom = '-100px';
			}

		}
	}
</script>
<style scoped>
	*{
		margin:0;
		padding:0;
		list-style: none;
	}
	.tab{
		position:relative;
		width:800px;
		height: 600px;
		overflow: hidden;
	}
	.top li{
		background-repeat: no-repeat;
		width:100%;
		height:100%;
		position: absolute;
		left:0;
		top:0;
	}
	.circle{
		background-color: rgba(0,0,0,0.3);
		border-radius: 10px;
		position: absolute;
		left:50%;
		transform: translateX(-50%);
		bottom: 7px;
		z-index: 3;
	}
	.circle li{
		width: 6px;
		height: 6px;
		background-color: white;
		border-radius: 3px;
		margin:7px;
		float: left;
	}
	.circle .active{
		background-color: orange;
	}
	.bottom{
		background-color: rgba(255,255,255,0.7);
		position: absolute;
		left:50%;
		transform: translateX(-50%);
		bottom:-100px;

	}
	.bottom li{
		width:72px;
		height: 70px;
		margin:15px 4px;
		float: left;
	}
</style>