<template>
	<div>
	<ul class="al">
		<li 
			class="item" 
			v-for="item of letters" 
			:key="item"
			:ref="item"
			@click="handleClick"
			@touchstart.prevent="handleTouchStart"
			@touchmove="handleTouchMove"
			@touchend="handleTouchEnd"
			>
			{{item}}
		</li>
	</ul>
	</div>
</template>

<script>
	export default {
		name:'CityAlphabet',
		props:{
			cities: Object
		},
		data () {
			return {
				touchStatus: false,
				startY: 0,
				timer: null
			}
		},
		updated () {
			this.startY = this.$refs['A'][0].offsetTop
		},
		methods: {
			handleClick (f) {
				this.$emit('change',f.target.innerText)
			},
			handleTouchStart () {
				this.touchStatus = true
			},
			handleTouchMove (f) {
				if(this.touchStatus) {
					if(this.timer){
						clearTimeout(this.timer)
					}
					this.timer=setTimeout(() => {
						const touchY = f.touches[0].clientY-79
					const index = Math.floor((touchY-this.startY)/22)
					if(index>= 0 && index<this.letters.length){
					this.$emit('change',this.letters[index])
					}
					},16)
				}
			},
			handleTouchEnd () {
				this.touchStatus = false
			},
		},
		computed:{
			letters () {
				const letters = []
				for (let i in this.cities) {
					letters.push(i)
				}
				return letters
			}
		}
	}
</script>

<style scoped>
	.al{
		display: flex;
		flex-direction: column;
		justify-content: center;
		position:absolute;
		right: 0;
		top: 1.58rem;
		bottom: 0;
		width: .4rem;
	}
	.item{
		text-align: center;
		line-height: .44rem;
		color:  #00bcd4;
	}

</style>