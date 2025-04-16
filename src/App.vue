<script setup lang="ts">
import TheCalculator from './components/TheCalculator.vue'
</script>

<template>
	<div id="calc">
		<TheCalculator/>
	</div>
</template>

<style scoped>
#calc {
	background-color: var(--White);
	border-radius: 10px;
	margin: auto;
	width: 40%;
}
</style>
