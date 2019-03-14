<template>
	<div>
		<city-header></city-header>
		<city-search :cities="cities"></city-search>
		<city-list 
			:cities="cities" 
			:hotCities="hotCities"
			:le="letter"
			></city-list>
		<city-alphabet 
			:cities="cities"
			@change="letterChange"
			></city-alphabet>
	</div>
</template>

<script>
	import CityHeader from './components/Header.vue'
	import CitySearch from './components/Search.vue'
	import CityList from './components/List.vue'
	import CityAlphabet from './components/Alphabet.vue'
	import axios from 'axios'
	export default {
		name:'City',
		components: {
			CityHeader,
			CitySearch,
			CityList,
			CityAlphabet
		},
		data () {
			return {
				cities: {},
				hotCities: [],
				letter: ''
			}
		},
		methods: {
			getCityInfo () {
				axios.get('./static/mock/city.json')
				.then(this.getCityInfoSucc)
			},
			getCityInfoSucc (res) {
				res=res.data
				if(res.ret&&res.data){
					const data= res.data
					this.cities=data.cities
					this.hotCities=data.hotCities
				}
			},
			letterChange (letter) {
				this.letter = letter
			}
		},
		mounted () {
			this.getCityInfo()
		}
	}
</script>

<style scoped>
	
</style>