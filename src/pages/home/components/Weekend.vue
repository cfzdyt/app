<template>
	<div>
		<div class="title">周末去哪儿</div>
		<ul>
			<li class="item border-bottom" v-for="item of list" :key="item.id">
				<div class="item-img-wrap">
				<img class="item-img" :src="item.imgUrl"/>
				</div>
				<div class="item-info">
					<p class="item-title">{{item.title}}</p>
					<p class="item-dec">{{item.desc}}</p>
					
				</div>
			</li>
		</ul>
	</div>
</template>

<script>
	export default{
		name:'HomeWeekend',
		data:function(){
			return {
			}
		},
		props: {
			list:Array
		}
	}
</script>

<style scoped>
	.title{
		text-indent: .2rem;
		line-height: .8rem;
		background: #eee;
		margin-top: .2rem;
	}
	.item-img-wrap{
		overflow: hidden;
		height: 0;
		padding-bottom: 37.1%;
	}
	.item-img{
		width: 100%;
		
	}
	.item-info{
		padding: .1rem;
		min-width: 0;
	}
	.item-title{
		line-height: .54rem;
		/*font-size: .32rem;*/
	}
	.item-dec{
		line-height: .4rem;
		color: #616161;
		overflow: hidden;
		white-space: nowrap;
		text-overflow: ellipsis;
	}
	
</style>