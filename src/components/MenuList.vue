<script setup>
const menuItems = [
	'О Simpeco',
	'Производство шин',
	'Продукты',
	'Сервис',
	'Контакты',
];
</script>

<template>
	<ul class="menu menu__list">
		<li v-for="item in menuItems" :key="item" class="menu__item">
			<a href="#!">{{ item }}</a>
		</li>
	</ul>
</template>

<style scoped lang="scss">

.menu__list {
	display: flex;
	flex-wrap: wrap;
	list-style-type: none;
	gap: 40px;
	margin: 0;
	padding: 0 20px;
}

.menu__item {
	cursor: pointer;
	font-weight: 500;

	&:hover,
	&:active,
	&:focus {
		color: $green;
	}
}
</style>
