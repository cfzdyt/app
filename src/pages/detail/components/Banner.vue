<template>
	<div>
		<div class="banner" @click="handelGallary">
			<img class="banner-img"
				:src="bannerImg" />
			<div class="banner-info">
				<div class="banner-number">
					<span class="iconfont">&#xe67b;</span>
					{{this.bannerImg.length}}</div>
				<div class="banner-title">{{this.sightName}}</div>
			</div>
		</div>
		<fade>
			<common-gallary 
				:imgs="gallaryImgs" 
				v-show="showGallary"
				@close="handelGallaryClose"
				></common-gallary>
		</fade>
	</div>
</template>

<script>
	import CommonGallary from 'common/gallary/Gallary.vue'
	import Fade from 'common/fade/Fade.vue'
	export default {
		name: 'DetailBanner',
		props: {
			sightName: String,
			bannerImg: String,
			gallaryImgs: Array,
			
		},
		data () {
			return{
			showGallary: false
			}
		},
		components: {
			CommonGallary,
			Fade
		},
		methods: {
			handelGallary () {
				this.showGallary = true
			},
			handelGallaryClose () {
				this.showGallary = false
			}
		}
		
	}
</script>


<style scoped>
	.banner{
		overflow: hidden;
		height: 0;
		padding-bottom: 55%;
		position: relative;
	}
	.banner-img{
		width: 100%;
	}
	.banner-info{
		position: absolute;
		left: 0;
		right: 0;
		bottom: 0;
		padding: 0 .3rem;
		color: #fff;
		background: linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,.8));
		
	}
	.banner-number{
		line-height: .4rem;
		height: .4rem;
		border-radius: .2rem;
		background: rgba(0,0,0,.5);
		width: 1.2rem;
		text-align: center;
	}
	.banner-title{
		font-size: .32rem;
		padding: .2rem 0;
	}
</style>