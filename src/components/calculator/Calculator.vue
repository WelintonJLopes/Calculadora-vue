<template>
	<v-container class="mt-10">
		<div cols="12" class="text-center pa-5 text-h5">Calculadora</div>
		<v-card width="320" class="mx-auto pa-4" rounded="md" color="#F5F5F5">
			<v-row no-gutters>
				<v-col cols="12">
					<Display />
				</v-col>
				<Button label="AC" cols="3" @onClick="clearMemory" />
				<Button label="/" cols="1" :operation="true" @onClick="setOperation" />
				<Button label="7" cols="1" @onClick="addDigit" />
				<Button label="8" cols="1" @onClick="addDigit" />
				<Button label="9" cols="1" @onClick="addDigit" />
				<Button label="*" cols="1" :operation="true" @onClick="setOperation" />
				<Button label="4" cols="1" @onClick="addDigit" />
				<Button label="5" cols="1" @onClick="addDigit" />
				<Button label="6" cols="1" @onClick="addDigit" />
				<Button label="-" cols="1" :operation="true" @onClick="setOperation" />
				<Button label="1" cols="1" @onClick="addDigit" />
				<Button label="2" cols="1" @onClick="addDigit" />
				<Button label="3" cols="1" @onClick="addDigit" />
				<Button label="+" cols="1" :operation="true" @onClick="setOperation" />
				<Button label="0" cols="2" @onClick="addDigit" />
				<Button label="." cols="1" @onClick="addDigit" />
				<Button label="=" cols="1" :operation="true" @onClick="setOperation" />
			</v-row>
		</v-card>
	</v-container>
</template>

<script>
import Button from "./components/Button.vue";
import Display from "./components/Display.vue";

export default {
	name: "Calculator",
	components: { Button, Display },
	methods: {
		clearMemory() {
			console.log("clear memory");
		},
		setOperation(operation) {
			console.log(operation);
		},
		addDigit(digit) {
			console.log(digit);
		},
	},
};
</script>