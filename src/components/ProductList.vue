<script setup lang="ts">
import { provide, ref } from 'vue'
import { Product, products } from '../data/products'
import Filter from './Filter.vue'
import ProductListItem from './ProductListItem.vue'

const filteredList = ref<Product[]>(products)
const filter = (id: number) => {
	if (id === -1) {
		filteredList.value = products
	} else {
		filteredList.value = products.filter((item) => item.brand === id)
	}
}

provide('filter', filter)
</script>

<template>
	<div class="container">
		<Filter />
		<TransitionGroup name="list" tag="ul" class="list">
			<ProductListItem
				v-for="item in filteredList"
				:key="item.id"
				:item="item"
			/>
		</TransitionGroup>
	</div>
</template>

<style scoped>
.list {
	list-style: none;
	margin: 0;
	padding: 0;
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	gap: 15px;
}

.container {
	display: grid;
	grid-template-columns: 1fr 7fr;
	column-gap: 40px;
	margin: 0 auto;
	max-width: 1440px;
}
.list-enter-active,
.list-leave-active {
	transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
	opacity: 0;
	transform: translateX(30px);
}
</style>
