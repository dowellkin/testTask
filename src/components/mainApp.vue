<template>
  <div class="main">
	<div class="posts">
		<div class="loading" v-if="posts.length == 0">
			<a-icon type="loading" />
		</div>
		<template v-else>
			<post
				username="johnWasya89"
				avatarPath='https://picsum.photos/32/32'
				:photoPath='this.getLink()'
				:likes='this.randomInteger(0,2000000)'
				:comments="[
					{ username: 'Veronica', message: 'Veridian Dynamics' },
					{ username: 'user2', message: 'so good' },
					{ username: 'some man4', message: 'what is it?' },
					{ username: 'Veronica', message: 'AWWWW' }
				]"
			/>
			<post
				username="johnWasya89"
				avatarPath='https://picsum.photos/32/32'
				:photoPath='this.getLink()'
				:likes='this.randomInteger(0,200000)'
				:comments="[{ username: 'Veronica', message: 'Veridian Dynamics' }]"
			/>
			<post
				username="johnWasya89"
				avatarPath='https://picsum.photos/32/32'
				:photoPath='this.getLink()'
				:likes='this.randomInteger(0,2000)'
				:comments="[{ username: 'Veronica', message: 'Veridian Dynamics' }]"
			/>
			<post
				username="johnWasya89"
				avatarPath='https://picsum.photos/32/32'
				:photoPath='this.getLink()'
				:likes='this.randomInteger(0,200)'
				:comments="[{ username: 'Veronica', message: 'Veridian Dynamics' }]"
			/>
			<post username="johnWasya89" avatarPath='https://picsum.photos/32/32' v-bind:photoPath='this.getLink()' :likes='this.randomInteger(0,2000)'/>
			<post username="johnWasya89" avatarPath='https://picsum.photos/32/32' v-bind:photoPath='this.getLink()' :likes='this.randomInteger(0,200)'/>
		</template>
	</div>
  </div>
</template>

<script>

import post from './post.vue'

export default {
	name: 'mainApp',
		components: {
			post,
		},
		props: {
			msg: String,
			posts: Object
		},
		methods: {
			getLink(){
				return `https://picsum.photos/${this.randomInteger(500,1200)}/${this.randomInteger(500,1200)}`
			},
			getRandomInt(max) {
				return Math.floor(Math.random() * Math.floor(max));
			},
			randomInteger(min, max) {
				let rand = min + Math.random() * (max + 1 - min);
				return Math.floor(rand);
			}
		}
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.main{
	padding: 0 25px 60px 25px;
	position: relative;
	z-index: 1;
	height: 100%;
	overflow-y: scroll;
	-ms-overflow-style: none;
	overflow: -moz-scrollbars-none;
}

.main::-webkit-scrollbar {
	width: 0;
}

.posts{
	height: 100%;
}

.loading{
	display: flex;
	justify-content: center;
	align-items: center;
	height: 100%;
	font-size: 64px;
}
</style>
