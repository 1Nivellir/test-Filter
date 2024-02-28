<script setup lang="ts">
import { defineProps, inject } from 'vue'

const props = defineProps({
	item: {
		type: Object,
		required: true,
	},
})
const filter = inject<(id: number) => void>('filter')
const item = props.item
</script>

<template>
	<div class="input__wrapper">
		<label :for="item.id"> {{ item.title }}</label>
		<input
			type="radio"
			:value="item.id"
			:id="item.id"
			name="filterName"
			@change.prevent="filter && filter(item.id)"
		/>
	</div>
</template>

<style scoped>
.input__wrapper {
	border-bottom: 1px solid grey;
	width: 100%;
}
</style>
