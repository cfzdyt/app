<template>
	<div class="container" @click="closeGallary">
		<div class="wrapper">
			<swiper :options="swiperOption">
			    <swiper-slide v-for="(item, index) in imgs" :key="index">
			    	<img 
			    class="swiper-img"	:src="item"/>
			    </swiper-slide>
		    	<div class="swiper-pagination"  slot="pagination"></div>
		  </swiper>
		</div>
		
	</div>
</template>

<script>
	export default {
		name: 'CommonGallary',
		data () {
			return {
				swiperOption: {
					pagination: '.swiper-pagination',
					paginationType: 'fraction',
					loop:true,
					observeParents: true,
					observer: true
					//自我刷新
				}
			}
		},
		props: {
			imgs: {
				type: Array,
				default () {
					return []
				}
			}
		},
		methods: {
			closeGallary () {
				this.$emit('close')
			}
		}
	}
	
</script>

<style scoped>
	.container >>> .swiper-container{
		overflow: inherit;
	}
	.container{
		display: flex;
		flex-direction: column;
		justify-content: center;
		position: fixed;
		left: 0;
		right: 0;
		top: 0;
		bottom: 0;
		background: #000;
		z-index: 3;
	}
	.wrapper{
		background: white;
		width: 100%;
		height: 0;
		padding-bottom: 62%;
	}
	.swiper-img{
		width: 100%;
	}
	.swiper-pagination{
		color: #fff;
		bottom: -3rem;
	}
</style>