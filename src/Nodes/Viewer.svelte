<script lang="ts">
	import { generateInput, generateOutput } from 'svelvet';
	import CustomNode from './CustomNode.svelte';
	import { get } from 'svelte/store';

	export let position: {
		x: number;
		y: number;
	} = { x: 0, y: 0 };

	type Input = {
		value: number;
	};

	const initialData = {
		value: 0
	};

	const inputs = generateInput(initialData);
</script>

<CustomNode
	label="Viewer"
	inputs={1}
	{position}
	width={150}
	height={150}
	inputsStore={inputs}
	inputKeys={['value']}
>
	{#if typeof get($inputs.value) === 'string' || typeof get($inputs.value) === 'number'}
		<b class="text-8xl">{get($inputs.value)}</b>
	{/if}
</CustomNode>
