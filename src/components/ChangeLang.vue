<script setup>
import { ref } from 'vue';

const navigateList = (direction) => {
	const currentIndex = languagesData.findIndex(
		(lang) => lang.value === selectedLanguage.value,
	);
	let nextIndex = currentIndex + direction;
	if (nextIndex < 0) {
		nextIndex = languagesData.length - 1;
	} else if (nextIndex >= languagesData.length) {
		nextIndex = 0;
	}
	selectedLanguage.value = languagesData[nextIndex].value;
};

const languagesData = [
	{ value: 'RU', text: 'RU' },
	{ value: 'CSY', text: 'CSY' },
	{ value: 'EN', text: 'EN' },
];

const defaultLanguage = 'RU';

const languages = ref(
	languagesData.filter((language) => language.value !== defaultLanguage),
);
const selectedLanguage = ref(defaultLanguage);
const isOpen = ref(false);

const toggleOpen = () => {
	isOpen.value = !isOpen.value;
	const menu = document.querySelector('.select__menu');
	if (isOpen.value) {
		menu.classList.add('is-open');
	} else {
		menu.classList.remove('is-open');
	}
};

const selectLanguage = (language) => {
	selectedLanguage.value = language;
	toggleOpen();
	languages.value = languagesData.filter((lang) => lang.value !== language);
};
</script>

<template>
	<div class="select">
		<div
			class="select__menu"
			@click="toggleOpen"
			@keydown.down="navigateList(1)"
			@keydown.up="navigateList(-1)"
			tabindex="0"
			@keyup.enter.stop="selectLanguage(selectedLanguage)"
		>
			<div class="select__option">
				{{ selectedLanguage }}
			</div>
			<ul v-show="isOpen" class="select__list">
				<li
					v-for="language in languages"
					:key="language.value"
					@click="selectLanguage(language.value)"
					tabindex="0"
					@keyup.enter.stop="selectLanguage(language.value)"
				>
					{{ language.text }}
				</li>
			</ul>
		</div>
	</div>
</template>

<style scoped lang="scss">
.select {
	position: relative;
	cursor: pointer;

	&:focus {
		color: $green;
	}
}

.select__menu {
	position: relative;
	background-color: $black-green;
	border: none;
	color: white;
	appearance: none;
	padding: 8px 30px 8px 10px;
	background-image: url("../images/icons/arrow-bottom.svg");
	background-repeat: no-repeat;
	background-position: 85% 50%;
	background-size: 18px 10px;
	font-weight: 500;
	font-size: 18px;
	outline: none;
}

.select__menu.is-open {
	background-image: url("../images/icons/arrow-top.svg");
}

.select__list {
	position: absolute;
	margin: 0;
	list-style-type: none;
	background-color: #587203;
	top: 68px;
	right: 0;
	border-radius: 0 0 20px 20px;
	padding: 0;
}

.select__list li {
	padding: 10px 24px;
	border: none;
	outline: none;
}

.select__option {
	position: relative;

}
</style>
