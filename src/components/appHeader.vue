<template>
	<div class="header">
		<div class="logo--container">
			<a class="logo--link" href="#" @click="changeMenuFunc(1)" >
				<img class="logo" src="@/assets/logo.svg" alt="logo">
			</a>
		</div>
	</div>
</template>

<script>
export default {
  name: 'appHeader',
  props: {
	changeMenuFunc: Function
    // msg: String
  }
}
</script>


<style>

.header{
	/* box-shadow: 0 1px 4px rgba(0,0,0,.2); */
	height: 64px;
}

.logo--link{
	display: block;
	height: 100%;
}
.logo--container{
	height: 100%;
}
.logo{
	height: 100%;
	filter: brightness(5);
}

</style>