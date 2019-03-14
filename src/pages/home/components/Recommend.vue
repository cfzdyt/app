<template>
	<div>
		<div class="title">热销推荐</div>
		<ul>
				<router-link  tag="li"
					class="item border-bottom" 
					v-for="item of list" 
					:key="item.id"
					:to="'/detail/'+ item.id"
					>
					<img class="item-img" :src="item.imgUrl"/>
					<div class="item-info">
						<p class="item-title">{{item.title}}</p>
						<p class="item-dec">{{item.desc}}</p>
						<button class="item-btn">查看详情</button>
					</div>
				</router-link>
		</ul>
	</div>
</template>

<script>
	export default{
		name:'HomeRecommend',
		data:function(){
			return {
				
			}
		},
		props: {
			list: Array
		}
	}
</script>

<style scoped>
	.title{
		text-indent: .2rem;
		line-height: .8rem;
		background: #eee;
	}
	.item{
		overflow: hidden;
		height: 1.9rem;
		display: flex;
	}
	.item-img{
		width: 1.7rem;
		height: 1.7rem;
		padding: .1rem;
	}
	.item-info{
		flex: 1;
		padding: .1rem;
		min-width: 0;
		
	}
	.item-title{
		line-height: .54rem;
		font-size: .32rem;
	}
	.item-dec{
		line-height: .4rem;
		color: #616161;
		overflow: hidden;
		white-space: nowrap;
		text-overflow: ellipsis;
	}
	.item-btn{
		line-height: .44rem;
		background: #ff9300;
		padding: 0 .2rem;
		border-radius:.06rem ;
		margin-top: .2rem;
		color: #fff;
	}
</style>