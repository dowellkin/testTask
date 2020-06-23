<template>
  <div id="app">
	<!--<a-button type="primary">Button></a-button> -->
	<a-layout :style="{position: 'relative', height: '100vh', padding: '0 0 64px 0'}">
		<a-layout-header>
			<appHeader :changeMenuFunc="this.changeMenuFunc"/>
		</a-layout-header>
		<a-layout-content :style="{ overflow: 'auto', height: '100%' }">
			<mainApp v-if="this.menu == 1" :posts='[1]'/>
			<search v-else-if="this.menu == 2" />
			<likes v-else-if="this.menu == 3" />
			<profile v-else-if="this.menu == 4" />
		</a-layout-content>
		<a-layout-footer :style="{padding: '0'}">
			<appFooter
				v-bind:menu='this.menu'
				v-bind:btns="['home', 'research', 'heart', 'user']"
				:changeMenuFunc="this.changeMenuFunc" />
		</a-layout-footer>
	</a-layout>
  </div>
</template>

<script>
import mainApp from './components/mainApp.vue'
import appHeader from './components/appHeader.vue'
import appFooter from './components/appFooter.vue'
import search from './components/search.vue'
import likes from './components/likes.vue'
import profile from './components/profile.vue'

export default {
	name: 'App',
	components: {
		mainApp,
		appHeader,
		appFooter,
		search,
		likes,
		profile
	},
	methods: {
		test(){
			console.log("succ");
		},
		changeMenuFunc(index){
			this.menu = index;
		}
	},
	data: function(){
		return {
			menu: 1
		}
	}
}
</script>

<style>
html{
	height: 100%;
}

body{
  background-color: rgb(245, 245, 245);
  height: 100%;
  overflow: hidden;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  max-width: 800px;
  margin: 0 auto;
  background-color: #fff;
  height: 100vh;
  position: relative;
}
</style>
