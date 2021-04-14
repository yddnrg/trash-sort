<template>
  <div id="app">
    <drawer-layout ref="drawer"
  :enable="true"
  :animatable="true"
  :z-index="0"
  :drawable-distance="Math.floor(800/3)"
  :content-drawable="true"
  :backdrop="true"
  :backdrop-opacity-range="[0,0.4]"
  @slide-start="handleSlideStart"
  @slide-move="handleSlideMove"
  @slide-end="handleSlideEnd"
  @mask-click="handleMaskClick">
      <div class="drawer" slot="drawer">
        <div class="text">This is drawer</div>
      </div>
      <div class="content" slot="content">
        <button href="javascript:void(0)" class="btn"
           @click="handleToggleDrawer">
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </button>
        <div class="text">trash sort</div>
      </div>
    </drawer-layout>
  </div>
</template>

<script>
import {DrawerLayout} from "vue-drawer-layout"
export default {
  name: 'app',
  components:{
    DrawerLayout
  },
  methods:{
     handleSlideStart() {
        console.info('slide-start');
      },
      handleSlideMove(position) {
        console.info('slide-move', position);
      },
      handleSlideEnd(visible) {
        console.info('slide-end', visible);
      },
      handleMaskClick() {
        console.info('mask-click');
        this.$refs.drawer.toggle(false);
      },
      handleToggleDrawer() {
        this.$refs.drawer.toggle();
      }
      
  }
}
</script>

<style>


/* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
} */

.content {
    position: relative;
    width: 100%;
    height: 100%;
    overflow: auto;
    background-color: #4b89c2;
}
.text {
    width: 80%;
    font-size: 50px;
    margin:0 auto;
    text-align: center;
    line-height: 250px;
    color: #fff;
}
.drawer {
    position: absolute;
    background-color: #ff9d7a;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
}
.btn {
    float: left; 
    padding: 9px 10px; 
    margin-top: 8px; 
    margin-right: 15px; 
    background-color: transparent; 
    border: 1px solid transparent; 
    outline: none;
}
.btn .icon-bar{
	display: block; 
	margin-top: 4px; 
	width: 22px; 
	height: 3px; 
	background: #ffffff; 
	border-radius: 1px;
}
</style>
