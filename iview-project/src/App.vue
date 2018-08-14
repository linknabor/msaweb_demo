<template>
  <div id="app" class="app-main">
  <keep-alive>
    <router-view/>
    </keep-alive>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style  scoped>
html,body{
	width:100%;
	height: 100%;
	background: #f0f0f0;
	overflow: hidden;
}
.app-main{
	width: 100%;
	height: 100%;
}
</style>
