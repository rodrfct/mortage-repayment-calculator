<script setup lang="ts">
import { ref, useTemplateRef } from 'vue';

const mortgageAmount = useTemplateRef<HTMLInputElement | null>('mortgage-amount')
const mortgageTerm = useTemplateRef<HTMLInputElement | null>('mortgage-term')
const mortgageInterestRate = useTemplateRef<HTMLInputElement | null>('mortgage-interest-rate')
const mortgageType = ref<(HTMLInputElement | null)[]>([])

const inputs = [ mortgageAmount, mortgageTerm, mortgageInterestRate ]

function handleSubmit() {
	let completed = true;

	for (const i  of inputs) {
		console.log(i.value)
		if (!i.value?.value.trim()) {
			completed = false;
			i.value?.parentElement?.classList.add("missing-field")
		}
	}

	for (const r of mortgageType.value) {
		console.log(r)
		if (r?.checked) {
			completed = false;
			break;
		} 
		r?.parentElement?.parentElement?.classList.add("missing-field")
		console.log(r?.parentElement?.parentElement)
	}
}
</script>

<template>
	<form @submit.prevent="handleSubmit">
		<hgroup>
			<h1>Mortgage Calculator</h1>
			<button type="reset">Clear All</button>
		</hgroup>

		<div class="input-wrapper">
			<label for="amount">Mortgage Amount</label>
			<div class="input-group">
				<span class="input-decor">£</span>
				<input ref="mortgage-amount" type="number" name="amount" id="amount">
			</div>
		</div>
		<div>
			<div class="input-wrapper">
				<label for="term">Mortgage Term</label>
				<div class="input-group">
					<input ref="mortgage-term" type="number" name="term" id="term" >
					<span class="input-decor">years</span>
				</div>
			</div>

			<div class="input-wrapper">
				<label for="interest-rate">Interest Rate</label>
				<div class="input-group">
					<input ref="mortgage-interest-rate" type="number" name="interest-rate" id="interest-rate" >
					<span class="input-decor">%</span>
				</div>
			</div>
		</div>
		<div class="radio-wrapper">
			<label for="type">Mortgage Type</label>
			<div class="radio-group">
				<input :ref="(el) => {mortgageType[0] = el}" type="radio" name="type" id="type" >
				<div class="fake-radio"></div>
				<span>Repayment</span>
			</div>
			<div class="radio-group">
				<input :ref="(el) => {mortgageType[1] = el}" type="radio" name="type" id="type" >
				<div class="fake-radio"></div>
				<span>Interest Only</span>
			</div>
		</div>
		<div>
			<button id="calculate">
				<img src="../assets/icons/icon-calculator.svg" alt="">
				Calculate Repayments
			</button>
		</div>
	</form>
</template>

<style scoped>
form {
	padding: 30px;
	display: flex;
	flex-direction: column;
	gap: 25px;
}

hgroup {
	display: flex;
	justify-content: space-between;

	& h1 {
		margin: 0;
		font-size: 1.3rem;
		color: var(--Slate-900)
	}

	& button {
		border: none;
		background-color: inherit;
		color: inherit;
		font-weight: 500;
		text-decoration: underline;
		cursor: pointer;
	}
}

label {
	display: block;
	margin-bottom: 10px;
}

.input-group {
	display: flex;
	border: 1px solid;
	border-radius: 5px;

	& span, input {
		border-radius: inherit;
	}

	& span {
		padding: .5em .8em;
		background-color: var(--Slate-100);
		font-weight: 600;
	}

	& input {
		width: 100%;
		border: none;
		outline: none;
		cursor: pointer;

		font-family: inherit;
		font-weight: 700;
		padding: 0 1em;
		color: var(--Slate-900);

		&[type=number] {
			appearance: textfield;

			&::-webkit-inner-spin-button,
			&::-webkit-outer-spin-button {
				-webkit-appearance: none;
				appearance: none;
				margin: 0;
			}
		}
	}

	&:has(input:focus-visible), &:hover {
		border-color: var(--Lime);

		span {
			background-color: var(--Lime);
			color: var(--Slate-900);
		}
	}
}

.radio-group {
	position: relative;
	border: 1px solid;
	border-radius: 5px;
	margin: 6px 0;
	padding: .5em;
	cursor: pointer;

	& span {
		margin: 0 7px;
		font-weight: 700;
		color: var(--Slate-900);
	}

	.fake-radio {
		display: inline-block;
		outline: 1px solid;
		outline-offset: 2px;
		aspect-ratio: 1/1;
		width: 10px;
		border-radius: 50%;
	}

	input[type=radio] {
		position: absolute;
		height: 100%;
		width: 100%;
		inset: 0;
		margin: 0;
		appearance: none;
		cursor: pointer;
	}
}

.radio-group:has(input:checked), .radio-group:hover {
	border-color: var(--Lime);
}

.radio-group:has(input:checked) {
	background-color: hsl(from var(--Lime) h s l / .25);
}

.radio-group:has(input:checked) {
	
	.fake-radio {
		outline-color: var(--Lime);
		background-color: var(--Lime);
	}

}

div:has(.input-wrapper) {
	display: flex;
	gap: 15px;
}

#calculate {
	padding: 8px 30px;
	display: flex;
	align-items: center;
	gap: .5em;
	font-weight: 700;
	color: var(--Slate-900);
	background-color: var(--Lime);
	border: none;
	border-radius: 30px;
	cursor: pointer;

	&:hover {
		background-color: hsl(from var(--Lime) h s l / .75);
	}
}

.input-wrapper, .radio-group, .fake-radio, span {
	transition-property: color border-color outline-color background-color;
	transition-duration: .3s;
}

.missing-field {
	border-color: var(--Red);

	input + span, span:first-child {
		color: var(--White);
		background-color: var(--Red);
	}

}

.input-wrapper:has(.missing-field)::after, .radio-wrapper.missing-field::after {
	content: "Field is required";
	display: inline-block;
	margin-top: .6em;
	color: var(--Red);
	font-weight: 500;
} 
</style>
