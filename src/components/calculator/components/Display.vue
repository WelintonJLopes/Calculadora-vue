<template>
	<v-sheet
		color="#212121"
		class="white--text text-right pa-5 text-h6 text-truncate"
		style="border: 1px solid black"
	>{{value}}</v-sheet>
</template>

<script>
export default {
	name: "Display",
	props: ["value"],
};
</script>