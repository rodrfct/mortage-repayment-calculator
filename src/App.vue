<script setup lang="ts">
import TheCalculator from './components/TheCalculator.vue'
import TheResult from './components/TheResult.vue';
</script>

<template>
	<div id="calc">
		<TheCalculator/>
		<TheResult/>
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

	@media (width < 375px) {
		grid-template-columns: 1fr;
	}
}
</style>
