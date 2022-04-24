<template>
	<v-container class="mt-10">
		<div cols="12" class="text-center pa-5 text-h5">Calculadora</div>
		<v-card width="320" class="mx-auto pa-4" rounded="md" color="#F5F5F5">
			<v-row no-gutters>
				<v-col cols="12">
					<Display :value="displayValue" />
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
	data: () => ({
		displayValue: "0",
		clearDisplay: false,
		operation: null,
		values: [0, 0],
		current: 0,
	}),
	methods: {
		clearMemory() {
			Object.assign(this.$data, this.$options.data());
		},
		setOperation(operation) {
			if (this.current === 0) {
				this.operation = operation;
				this.current = 1;
				this.clearDisplay = true;
			} else {
				const equals = operation === "=";
				const currentOperation = this.operation;

				try {
					this.values[0] = eval(
						`${this.values[0]} ${currentOperation} ${this.values[1]}`
					);
				} catch (e) {
					this.$$emit("OnError", e);
				}

				this.values[1] = 0;

				this.displayValue = this.values[0];
				this.operation = equals ? null : operation;
				this.current = equals ? 0 : 1;
				this.clearDisplay = !equals;
			}
		},
		addDigit(digit) {
			if (digit === "." && this.displayValue.includes(".")) {
				return;
			}

			const clearDisplay = this.displayValue === "0" || this.clearDisplay;
			const currentValue = clearDisplay ? "" : this.displayValue;
			const displayValue = currentValue + digit;

			this.displayValue = displayValue;
			this.clearDisplay = false;

			if (digit !== ".") {
				this.values[this.current] = parseFloat(displayValue);
			}
		},
	},
};
</script>