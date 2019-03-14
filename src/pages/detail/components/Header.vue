<template>
	<div>
		<router-link 
			tag="div"
			to="/" 
			class="header-abs"
			v-show="showAbs"
			>
			<div class="header-abs">
				<div class="iconfont back-icon">&#xe624;</div>
			</div>
		</router-link>
		<div 
			class="header-fixed"
			v-show="!showAbs"
			:style="opacityStyle"
			>
			景点详情
			<router-link to="/" >
				<div class="iconfont back-icon-fixed">&#xe624;</div>
			</router-link>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'DetailHeader',
		data () {
			return {
				showAbs : true,
				opacityStyle: {
					opacity:0
				}
			}
		},
		activated () {
			console.log('p')
			window.addEventListener('scroll',this.handleScroll)
		},
		deactivated () {
			window.removeEventListener
			//页面隐藏时时解绑全局事件
		},
		methods:{
			handleScroll () {
				const top=document.documentElement.scrollTop
				if (top>60) {
				let opacity=top/140
				opacity=opacity >1 ? 1 : opacity
					this.opacityStyle={
						opacity
					}
                    
					this.showAbs = false
				}else{
					this.showAbs = true
				}
			}
		}
		
	}
</script>

<style scoped>
.header-abs{
	position: absolute;
	left: 0;
	top: 0;
	width: .8rem;
	height: .8rem;
	line-height: .8rem;
	border-radius: .4rem;
	background: rgba(0,0,0,.3);
	text-align: center;
	
}
.back-icon{
	color: #fff;
	height: .8rem;
	
}
.back-icon-fixed{
		width: .64rem;
		text-align: center;
		font-size: .4rem;
		position: absolute;
		top: 0;
		left: 0;
		color: #fff;
		
}
.header-fixed{
		height: .86rem;
		line-height: .86rem;
		text-align: center;
		color: #fff;
		background: #00bcd4;
		font-size: .4rem;
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		z-index: 2;
	}

</style>