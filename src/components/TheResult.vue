<script setup lang="ts">
import type { ResultInterface } from '@/App.vue';

const props = <ResultInterface>defineProps(['result'])
</script>

<template>
	<div v-if="!result.total" id="result" class="empty">
		<img src="@/assets/icons/illustration-empty.svg" alt="">
		<div class="text">
			<h2>Results shown here</h2>
			<p>
				Complete the form and click “calculate repayments” to see what
				your monthly repayments would be.
			</p>
		</div>
	</div>
	<div v-else id="result">
		<h2>Your results</h2>
		<p>
			Your results are shown below based on the information you provided. 
			To adjust the results, edit the form and click “calculate repayments” again.
		</p>
		<div class="repayments">
			<div id="shadow"></div>
			<h3>Your monthly repayments</h3>
			<span id="monthly">£{{ result.monthly.toLocaleString() }}</span>
			<hr>
			<h3>Total you'll repay over the term</h3>
			<span id="term">£{{ result.total.toLocaleString() }}</span>
		</div>
	</div>
</template>

<style scoped>
#result {
	border-radius: inherit;
	border-top-left-radius: 0;
	border-bottom-left-radius: 60px;
	background-color: var(--Slate-900);
	color: var(--Slate-300);
	padding: 15px 25px;

	&.empty {
		text-align: center;
		padding: 80px 30px;
	}

	& h2 {
		color: var(--White);
	}

	@media (width < 400px) {
		border-radius: 0;
	}

}

.repayments {
	background-color: hsl(from var(--Slate-900) h s 12%);
	padding: 25px;
	border-radius: 7px;
	box-shadow: 0 3px var(--Lime) inset;

	h3 {
		color: var(--Slate-500);
		font-size: 1rem;
		font-weight: 500;
		margin-bottom: 5px;
		margin-top: 0;
	}

	span {
		display: block;
	}

	#monthly {
		font-size: 3em;
		font-weight: 700;
		color: var(--Lime);
	}

	#term {
		font-size: 1.2em;
		font-weight: 700;
		color: var(--White);
	}

	hr {
		color: var(--Slate-700);
		margin: 25px 0;
	}
}
</style>
