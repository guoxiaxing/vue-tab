<template>
	<div class='slider'>
		<ul class='top' @click='change'>
			<li v-for='(v,i) in imgs' :style='{backgroundImage:"url("+v+")",backgroundSize:"cover"}' :class='allclass[i]'></li>
		</ul>
	</div>
</template>
<script>
	export default{
		props:['slider'],
		data(){
			return {
				imgs:[],
				allclass:[]
			}
		},
		created(){
			this.imgs = this.slider.imgs;
			for(var i=0;i<this.imgs.length;i++){
				this.allclass.push('s'+i);
			}
		},
		methods:{
			change(){
				this.allclass.push(this.allclass.shift());
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
	.slider{
		position: relative;
	}
	.top{
		height: 200px;
	}
	.top li{
		width: 300px;
		height: 100%;
		position: absolute;
		transform: perspective(800px);
		left:50%;
		top:0;
	}
	.top .s0{
		transform: perspective(800px) translate(-50%) rotateY(90deg);
		margin-left: -450px;
		opacity: 0;
		transition: 0.7s;
	}
	.top .s1{
		transform: perspective(800px) translate(-50%) rotateY(60deg);
		margin-left: -300px;
		opacity: 0.6;
		transition: 0.7s;
	}
	.top .s2{
		transform: perspective(800px) translate(-50%) rotateY(30deg);
		margin-left: -150px;
		opacity: 0.8;
		transition: 0.7s;
	} 
	.top .s3{
		transform: translate(-50%) perspective(800px);
		z-index:5;
		transition: 0.7s;
	}
	.top .s6{
		transform: perspective(800px) translate(-50%) rotateY(-90deg);
		margin-left: 450px;
		opacity: 0;
		transition: 0.7s;
	}
	.top .s5{
		transform: perspective(800px) translate(-50%) rotateY(-60deg);
		margin-left: 300px;
		opacity: 0.6;
		transition: 0.7s;
	}
	.top .s4{
		transform: perspective(800px) translate(-50%) rotateY(-30deg);
		margin-left: 150px;
		opacity: 0.8;
		transition: 0.7s;
	} 
</style>