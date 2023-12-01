<script lang="ts">
	import { Slider, generateInput, generateOutput } from 'svelvet';
	import CustomNode from './CustomNode.svelte';

	export let position: {
		x: number;
		y: number;
	} = { x: 0, y: 0 };

	type Inputs = {
		value: number;
	};
	const initialData = {
		value: 0
	};

	const inputs = generateInput(initialData);

	const procesor = (inputs: Inputs) => inputs.value;
	const output = generateOutput(inputs, procesor);
</script>

<CustomNode
	label="Number"
	outputs={1}
	width={250}
	height={90}
	{position}
	inputsStore={inputs}
	outputStore={output}
>
	<div class="m-2">
		<Slider parameterStore={$inputs.value} min={-50} max={50} />
	</div>
</CustomNode>
