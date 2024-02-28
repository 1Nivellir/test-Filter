<script setup lang="ts">
import { defineProps } from 'vue'
const props = defineProps({
	item: {
		type: Object,
		required: true,
	},
})
const item = props.item
</script>
<template>
	<li class="list__item item">
		<img :src="item.image" :alt="item.title" style="margin-bottom: 10px" />
		<h2 class="item__title">
			{{ item.title }}
		</h2>
		<span class="item__brand">Brand {{ item.brand }}</span>
		<span class="item__price">Цена: {{ item.regular_price.value }}</span>
		<span class="item__price">{{ item.regular_price.currency }}</span>
	</li>
</template>

<style scoped>
.list__item {
	position: relative;
	border: 1px solid grey;
	border-radius: 0.3rem;
	padding: 15px;
	height: max-content;
}
.item__title {
	margin: 0;
	margin-bottom: 10px;
	font-size: 18px;
}
.item__price {
	font-size: 14px;
}
.item__price:not(:last-child) {
	margin-right: 5px;
}
.item__brand {
	position: absolute;
	top: 10px;
	right: 10px;
	font-size: 18px;
	font-style: italic;
}
</style>
