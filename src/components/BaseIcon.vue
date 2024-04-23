<script setup>
defineProps({
	id: {
		type: String,
		required: true,
	},
});
</script>

<template>
	<svg focusable="false">
		<use :href="`/images/icons/${id}.svg`" />
	</svg>
</template>

<style lang="scss" scoped>
svg {
	fill: currentColor;
}
</style>
