<template>
  <div id="app">
    <keep-alive exclude="Detail">
    	<!--第二种解决方法剔除detail来获取请求-->
    	<router-view/>
    </keep-alive>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>

</style>
