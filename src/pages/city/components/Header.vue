<template>
	<div class="header">
	城市选择
		<router-link to="/">
			<div class="iconfont header-icon">&#xe624;</div>
		</router-link>
	</div>
	</div>
</template>

<script>
	export default {
		name:'CityHeader'
	}
</script>

<style scoped>
	.header{
		height: .86rem;
		line-height: .86rem;
		text-align: center;
		color: #fff;
		background: #00bcd4;
		font-size: .4rem;
		position: relative;
	}
	.header-icon{
		width: .64rem;
		text-align: center;
		font-size: .4rem;
		position: absolute;
		top: 0;
		left: 0;
		color: #fff;
	}
</style>