<script setup>
import ChangeLang from './ChangeLang.vue';
import BaseLogo from './BaseLogo.vue';
import MenuList from './MenuList.vue';
</script>

<template>
	<header class="header">
		<div class="header__inner container">
			<div class="header__container">
				<BaseLogo />
				<MenuList />
			</div>
			<ChangeLang />
		</div>
	</header>
</template>

<style scoped lang="scss">
.header {
	background-color: $black-green;
	padding: 30px 0;
	z-index: 10;
}
.header__inner {
	display: flex;
	align-items: center;
	justify-content: space-between;
}

.header__button select {
	padding: 5px;
}

.header__container {
	display: flex;
	align-items: center;
}
</style>
