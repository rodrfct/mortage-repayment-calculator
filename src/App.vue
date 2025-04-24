<script setup lang="ts">
import { ref } from 'vue';
import TheCalculator from './components/TheCalculator.vue'
import TheResult from './components/TheResult.vue';

export interface ResultInterface {
	total: number,
	monthly: number
}

const result = ref<ResultInterface>({
	total: 0,
	monthly: 0
})

const algo = ref(3)
</script>

<template>
	<div id="calc">
		<TheCalculator @calculate="(newVal) => result = newVal"/>
		<TheResult :result="result"/>
	</div>
</template>

<style scoped>
#calc {
	display: grid;
	grid-template-columns: 1fr 1fr;
	background-color: var(--White);
	border-radius: 20px;
	margin: auto;
	max-width: 900px;

	@media (width < 400px) {
		border-radius: 0;
		grid-template-columns: 1fr;
	}
}
</style>
