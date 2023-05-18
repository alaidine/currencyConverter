<script lang="ts">
	import Input from "./lib/Input.svelte"
</script>

<main>
	<form>
		<div>
			<Input value="value to be converted" />
			<select>
				<option>euro</option>
				<option>dollar</option>
			</select>
		</div>

		<div>
			<Input value="converted value" />
			<select>
				<option>euro</option>
				<option>dollar</option>
			</select>
		</div>
	</form>
</main>

<style>
</style>
