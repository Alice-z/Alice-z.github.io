<template>
<div id="app" >
	<div id="box" :style="{width ,border:width=='100%'?'none':'1px solid #ccc'}">
		<div  class="left"  :style="{left:width=='100%'?'50%':'75%' }">
			<img class="zoom" src="/static/img/lufei.jpg" width="100" height="100" style="border-radius: 50%" >
			<h1  >A l i c e</h1>
			<p><a  @click="width = width == '100%' ? '20%' : '100%'">Hmoe</a></p>
			<p><router-link to="blog">Blog</router-link></p>
			<p><router-link to="life" >Life</router-link></p>
			<p><a >Design by myself</a></p>
		</div>
	</div>
  <transition name="fade">
    <router-view  class="right" :style="{marginLeft:width }" />  
  </transition>
	<canvas :style="{left:width=='100%'?0:'20%' }" />
</div>

</template>
<script>
export default {
	data: _ => ({ width: '100%'}),
	mounted: _ => import('./unit/canvas.js')
}

</script>

<style>
@import url('/static/css/mixin.css');
html,
body,
#app{
 height:100%
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity .5s
}
.fade-enter,
.fade-leave-to {
  opacity: 0
}
#box{
height:100%;
position:relative;
}
.left {
  position: absolute;
  text-align: center;
  top: 50%;
  left: 50%;
  margin-left: -160px;
  margin-top: -160px;
  -webkit-user-select: none;
  -moz-user-select: none;
  user-select: none;
}
canvas {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
}
.right {
	height: 100%;
	background: transparent;
	position: relative;
}
</style>
