<template>
	<div class="icons">
		<swiper :options="swiperOption" >
			<swiper-slide v-for="(page,index) of pages" :key="index">
				<div class="icons-item" v-for="item of page" :key="item.id">
					<div class="icons-position">
						<img class="icons-img" :src="item.imgUrl"/>
					</div>
					<p class="icons-dec">{{item.desc}}</p>
				</div>
			</swiper-slide>
		
		 </swiper>
		
	</div>
</template>

<script>
	export default{
		name:'HomeIcons',
		data: function(){
			return {
				swiperOption:{
					autoplay:false
				}
				}
			
		},
		props: {
			list:Array
		},
		computed: {
			pages:function(){
				const pages=[]
				this.list.forEach((item,index) => {
					const page=Math.floor(index/8)
					if(!pages[page]){
						pages[page] = []
					}
					pages[page].push(item)
				})
				return pages
			}
		}
	}
</script>

<style scoped>
.icons >>> .swiper-container{
	height: 0;
	padding-bottom: 50%;
}
.icons{
	height: 0;
	padding-bottom: 50%;
	overflow: hidden;
	}
.icons-item{
	position: relative;
	float: left;
	width: 25%;
	height: 0;
	padding-bottom: 25%;
	
	overflow: hidden;
	
}
.icons-position{
	position: absolute;
	top: 0;
	left: 0;
	right: 0;
	bottom: .44rem;
	box-sizing: border-box;
	padding: .1rem;
}
.icons-img{
	height: 100%;
	margin: 0 auto;
	display: block;
}
.icons-dec{
   text-align: center;
	font-size: ;
	height: .44rem;
	line-height: .44rem;
	color: #333;
	position: absolute;
	bottom: 0;
	left: 0;
	right: 0;
	overflow: hidden;
	white-space: nowrap;
	text-overflow: ellipsis;
	
}
</style>