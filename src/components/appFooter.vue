<template>
	<div class="footer">
		<div class="buttons">
			<!-- <div v-for="(btn, index) in btns" v-bind:key="btn" class="button" @click="changeMenu(index+1)">
				<img v-if="menu != index+1" v-bind:src="'@/assets/home.svg'" :alt="btn" width="32" height="32">
				<img v-else src="'img/home-run.svg'" :alt="btn" width="32" height="32">
			</div> -->
			<!-- пыталя генерировать на основе полученного объекта, но не смог из-за использования @ в пути, он не парсится вью, из-за чего выходит неправильный путь -->
			<div class="button" @click="changeMenuFunc(1)">
				<img v-show="menu != 1" src="@/assets/home.svg" alt="home" width="32" height="32">
				<img v-show="menu == 1" src="@/assets/home-run.svg" alt="home" width="32" height="32">
			</div>
			<div class="button" @click="changeMenuFunc(2)">
				<img v-show="menu != 2" class="mirror-x" src="@/assets/research.svg" alt="research" width="32" height="32">
				<img v-show="menu == 2" src="@/assets/research-run.svg" alt="research" width="32" height="32">
			</div>
			<div class="button" @click="changeMenuFunc(3)">
				<img v-if="menu != 3" src="@/assets/heart.svg" alt="heart" width="32" height="32">
				<img v-else src="@/assets/heart-run.svg" alt="heart" width="32" height="32">
			</div>
			<div class="button" @click="changeMenuFunc(4)"  >
				<img v-if="menu != 4" src="@/assets/user.svg" alt="user" width="32" height="32">
				<img v-else src="@/assets/user-run.svg" alt="user" width="32" height="32">
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'appFooter',
	props: ['menu', 'btns', 'changeMenuFunc']
}
</script>

<style>

.footer{
	position: absolute;
	bottom: 0;
	left: 0;
	right: 0;
	z-index: 50;
}

.buttons{
	display: flex;
	justify-content: space-between;
	align-items: center;
	box-shadow: 0 -1px 4px rgba(0,0,0,.2);
	user-select: none;
	background-color: #fff;
}
.button{
	flex-grow: 1;
	height: 64px;
	display: flex;
	justify-content: center;
	align-items: center;
	cursor: pointer;
}
.button:not(:last-child){
	border-right: 1px solid rgba(0,0,0,.15);;
}
.button:hover{
	background-color: rgba(0,0,0,.1);
}
.button:active{
	background-color: rgba(0,0,0,.2);
}
.mirror-x{
	transform: scale(-1, 1);
}

</style>