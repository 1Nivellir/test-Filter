<script setup lang="ts">
import { inject } from 'vue'
import { brandsList } from '../data/brands'
import FilterItem from './FilterItem.vue'

const filter = inject<(id: number) => void>('filter')
</script>

<template>
	<aside>
		<nav>
			<form class="filter__form">
				<FilterItem v-for="item in brandsList" :key="item.id" :item="item" />
			</form>

			<button @click.prevent="filter && filter(-1)" class="btn__cancel">
				Сбросить фильтр
			</button>
		</nav>
	</aside>
</template>

<style scoped>
.filter__form {
	display: grid;
	grid-template-columns: 1fr;
	row-gap: 25px;
	margin-bottom: 20px;
}
.btn__cancel {
	border: none;
	background: blueviolet;
	padding: 10px 15px;
	border-radius: 0.3rem;
	font-weight: 600;
	color: #fff;
	font-size: 16px;
	transition: transform 0.3s ease-in-out, background 0.3s ease-in-out,
		color 0.3s ease-in-out;
}
.btn__cancel:focus-visible {
	outline: none;
}
.btn__cancel:hover {
	color: black;
	background: aqua;
}
.btn__cancel:active {
	transform: scale(0.95);
}
</style>
