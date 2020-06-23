<template>
	<div class="post">
		<div class="post-header">
			<a-avatar class="avatar" shape="square" :src="avatarPath" :size="48" icon="user" />
			<span class="username">{{username}}</span>
		</div>
		<div class="content">
			<div class="img-wrapper">
				<img class='post-img' :src="photoPath" alt="post picture">
			</div>
		</div>
		<div class="btns-wrapper">
			<div class="likes" @click="postLiked()">
				<a-icon class="like" v-if="liked" type="heart" theme='filled' :style="{ color: '#f36b6b' }"/>
				<a-icon class="like" v-else type="heart" />
				<span class="likes--count">{{normalizeLikes}}</span>
			</div>
			<div class="comments" @click="showAll">
				<a-icon type="message" />
			</div>
		</div>
		<div class="message">
			<template v-if="message">
				<span class="username--bold">{{username}}</span>
				{{message}}
			</template>
			<singleComment v-if="message" :username='username' :messsage='message' :link='"#"' />
			<template v-if="!showComments && comments.length > 3" >
				<singleComment
					v-for="comm in firstComments"
					v-bind:key="comm"
					:username="comments[comm].username"
					:message="comments[comm].message"
					:link='"#"'
				/>
				<div class="showAllComments" @click="showAll">Показать все комментарии</div>
			</template>
			<template v-if="showComments || comments.length < 4" >
				<singleComment
					v-for="comm in comments"
					v-bind:key="comm"
					:username="comm.username"
					:message="comm.message"
					:link='"#"'
				/>
			</template>
		</div>
	</div>
</template>

<script>
import singleComment from './oneSingleComment.vue'

export default {
	name: 'post',
	components: {
		singleComment
	},
	props: {
		username: String,
		avatarPath: String,
		photoPath: String,
		likes: Number, 
		liked: Boolean,
		comments: Object
	},
	methods: {
		postLiked(){
			if(this.liked){
				this.likes -= 1;
			} else {
				this.likes += 1;
			}
			this.liked = !this.liked;
		},
		showAll(){
			this.showComments = true;
		}
	},
	computed: {
		normalizeLikes: function (){
			const letters = ['', 'K', 'M'];
			const length = Math.floor((this.likes + "").length / 4);
			if(length > 0)
				return (this.likes / Math.pow(10, length*3) ).toFixed(1) + letters[length];
			else 
				return this.likes;
		}
	},
	data: function (){
		return {
			showComments: false,
			firstComments: [0,1,2]
		}
	}
}
</script>

<style>

.btns-wrapper{
	margin-top: 10px;
	display: flex;
	align-items: center;
}

.likes{
	display: flex;
	align-items: center;
	cursor: pointer;
}

.comments{
	margin-left: 30px;
	cursor: pointer;
}
.like, .comments{
	font-size: 32px;
	transition: color .2s ease;
}
.comments:hover{
	color: #6bb4f3;
}
.likes:hover .like{
	color: #f36b6b;
}

.likes--count{
	font-size: 24px;
	margin-left: 7px;
	user-select: none;
}

.post {
	padding: 10px 0;
}

.post-header{
	padding: 10px 0;
	display: flex;
	align-items: center;
}

.avatar{
	cursor: pointer;
}


.username{
	font-size: 24px;
	margin-left: 15px;
	cursor: pointer;
}

.username:hover{
	color: #3438c5b3;
}

.post-img{
	object-fit: contain;
	height: 100%;
	width: 100%;
}

.username--bold{
	cursor: pointer;
	font-weight: bold;
}

.showAllComments{
	cursor: pointer;
	font-size: 14px;
}
</style>