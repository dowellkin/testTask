<template>
	<div class="comment">
		<span class="username--bold"><a :href='link'>{{username}}</a></span>
		{{message}}
	</div>
</template>

<script>
export default {
	name: 'comment',
	props: {
		username: String,
		link: String,
		message: String
	}
}
</script>

<style>

.username--bold{
	cursor: pointer;
	font-weight: bold;
}
</style>