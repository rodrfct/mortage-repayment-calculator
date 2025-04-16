<script lang="ts">
</script>

<template>
	<form action="">
		<hgroup>
			<h1>Mortgage Calculator</h1>
			<button type="button">Clear All</button>
		</hgroup>

		<div>
			<label for="amount">Mortgage Amount</label>
			<div class="input-group">
				<span class="input-decor">£</span>
				<input type="number" name="amount" id="amount">
			</div>
		</div>
		<div>
			<div class="input-wrapper">
				<label for="term">Mortgage Term</label>
				<div class="input-group">
					<input type="number" name="term" id="term">
					<span class="input-decor">years</span>
				</div>
			</div>

			<div class="input-wrapper">
				<label for="interest-rate">Interest Rate</label>
				<div class="input-group">
					<input type="number" name="interest-rate" id="interest-rate">
					<span class="input-decor">%</span>
				</div>
			</div>
		</div>
		<div>
			<label for="type">Mortgage Type</label>
			<div class="radio-wrapper">
				<input type="radio" name="type" id="type">
				<span>Repayment</span>
			</div>
			<div class="radio-wrapper">
				<input type="radio" name="type" id="type">
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
	}
}

label {
	display: block;
	margin-bottom: 10px;
}

.input-group {
	display: flex;
	border: 1px solid;
	border-radius: 3px;

	& span {
		padding: .5em .8em;
		background-color: var(--Slate-100);
		font-weight: 600;
	}

	& input {
		width: 100%;
		border: none;

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
}

.radio-wrapper {
	border: 1px solid;
	border-radius: 2px;
	margin: 6px 0;
	padding: .5em;

	& span {
		margin: 0 7px;
		font-weight: 700;
		color: var(--Slate-900);
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
}
</style>
