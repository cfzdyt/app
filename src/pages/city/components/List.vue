<template>
	<div class="list" ref="wrapper">
		<div>
			<div class="item">
				<div class="title border-topbottom">当前城市</div>
				<div class="btn-list">
					<div class="btn-wrap">
						<div class="btn">{{this.$store.state.city}}</div>
					</div>
				</div>
			</div>
			<div class="item ">
				<div class="title border-topbottom">热门城市</div>
				<div class="btn-list">
					<div class="btn-wrap" 
						v-for="item of hotCities" 
						:key="item.id"
						@click="cityChange(item.name)"
						>
						<div class="btn">{{item.name}}</div>
					</div>
				</div>
			</div>
			<div 
				class="item" 
				v-for="(item,key) of cities" 
				:key="key"
				:ref="key"
				>
				<div class="title border-topbottom">{{key}}</div>
				<div class="item-list">
					<div class="item-list-l border-bottom" 
						v-for="innerItem of item" 
						:key="innerItem.id"
						@click="cityChange(innerItem.name)">
						{{innerItem.name}}
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	import BScroll from 'better-scroll'
	export default {
		name:'CityList',
		mounted () {
			this.scroll = new BScroll(this.$refs.wrapper)
		},
		watch: {
			le () {
				if(this.le){
					const element=this.$refs[this.le][0]
					this.scroll.scrollToElement(element)
				}
			}
		},
		methods: {
			cityChange (city) {
				this.$store.commit('changeCity',city)
				this.$router.push('/')
			}
		},
		props: {
			cities: Object,
			hotCities: Array,
			le: String
		},
	}
</script>

<style>
	.list{
		position: absolute;
		top: 1.58rem;
		left: 0;
		right: 0;
		bottom: 0;
		overflow: hidden;
	}
	.title{
		line-height: .54rem;
		font-size: .26rem;
		background: #eee;
		padding-left: .2rem;
		color: #666;
	}
	.btn-list{
		padding: .1rem .6rem .1rem .1rem ;
		overflow: hidden;
	}
	.btn-wrap{
		float: left;
		width: 33.33%;
	}
	.btn{
		padding: .1rem;
		text-align: center;
		margin: .1rem;
		border: .02rem solid #ccc;
		border-radius: .06rem;
	}
	.item-list-l{
		line-height: .76rem;
		color: #666;
		padding-left: .2rem;
	}
	.border-bottom::before{
		border-color: #ccc;
	}
	.border-topbottom::before,
	.border-topbottom::after{
		border-color: #ccc;
	}
</style>