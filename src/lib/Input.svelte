<script>
	export let value;

	const fs = require("fs")
	let currencies = [];
</script>

<div>
	<!-- svelte-ignore a11y-label-has-associated-control -->
	<label>{value}</label>
	<input type="text">

	<select>
		<option>euro</option>
	</select>
</div>
