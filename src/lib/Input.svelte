<script>
	import axios from "axios"
	import { currencies_name } from "./currencies_name.js"

	let value;
	let selected;
	let otherSelected
	let inputValue;
	let outputValue;
	let convertRate;
	let currency = "USD";
	let convertedCurrency = "USD"; 

	async function getConvertRate(currency, convertedCurrency) {
		const url = ` https://v6.exchangerate-api.com/v6/71f78204cab2a73255f815c1/latest/${currency}`

		const res = await axios.get(url)
		.then(response => {
			return response.data.conversion_rates[convertedCurrency]
		})
		.catch(error => {
			console.log(error)
		})

		return res
	}

	function onCurrencyChange() {
			console.log(`currency option has been changed from ${currency} to ${selected}`)
			currency = selected;
	}

	function onConvertedCurrencyChange() {
			console.log(`converted currency option has been changed from ${convertedCurrency} to ${otherSelected}`)
			convertedCurrency = otherSelected;
	}

	async function onClick() {
		convertRate = await getConvertRate(currency, convertedCurrency)
		console.log(convertRate)

		outputValue = isNaN(convertRate*parseInt(inputValue)) ? "invalid input" : convertRate*parseInt(inputValue) 
	}
</script>

<div>
		<input placeholder="currency" bind:value={inputValue} type="text">


		<select bind:value={selected} on:change={onCurrencyChange}>
			{#each currencies_name as currency}
				<option>{currency}</option>
			{/each}
		</select>

		<input placeholder="converted currency" bind:value={outputValue} type="text" readonly>


		<select bind:value={otherSelected} on:change={onConvertedCurrencyChange}>
			{#each currencies_name as currency}
				<option>{currency}</option>
			{/each}
		</select>

		<button on:click|preventDefault={onClick}>convert</button>
</div>
