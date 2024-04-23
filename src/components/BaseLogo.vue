<script setup>
const MoveOnIndex = () => {
	window.location.href = 'index.html';
};
</script>

<template>
	<img @click="MoveOnIndex" class="logo" src="/images/logo.png" alt="logo" />
</template>

<style scoped lang="scss">
.logo {
	width: 159px;
	height: 41px;
	color: black;
	cursor: pointer;
	margin-right: 130px;
}
</style>
