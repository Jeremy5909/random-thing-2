<script lang="ts">
	import { RadioGroup, generateInput, generateOutput } from 'svelvet';
	import CustomNode from './CustomNode.svelte';
	import { get } from 'svelte/store';

	export let position: {
		x: number;
		y: number;
	} = { x: 0, y: 0 };

	type Input = {
		value1: number;
		value2: number;
		option: string;
	};

	const initialData = {
		value1: 0,
		value2: 0,
		option: 'add'
	};

	const inputs = generateInput(initialData);
	const processor = (inputs: Input) => {
		switch (inputs.option.toLowerCase()) {
			case 'add':
				return inputs.value1 + inputs.value2;
			case 'subtract':
				return inputs.value1 - inputs.value2;
			case 'multiply':
				return inputs.value1 * inputs.value2;
			case 'divide':
				return inputs.value1 / inputs.value2;
			default:
				return 0;
		}
	};

	const output = generateOutput(inputs, processor);
</script>

<CustomNode
	label="Math"
	inputs={2}
	outputs={1}
	{position}
	inputsStore={inputs}
	outputStore={output}
	inputKeys={['value1', 'value2']}
	width={350}
	height={80}
>
	<div class="radio-group font-bold">
		<RadioGroup
			options={['ADD', 'SUBTRACT', 'MULTIPLY', 'DIVIDE']}
			parameterStore={$inputs.option}
		/>
	</div>
</CustomNode>
