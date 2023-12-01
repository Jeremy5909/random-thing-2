<script lang="ts">
	import { text } from '@sveltejs/kit';
	import { get } from 'svelte/store';
	import { Anchor, Node, Resizer, generateOutput } from 'svelvet';

	export let position: {
		x: number;
		y: number;
	} = { x: 0, y: 0 };

	export let width: number = 100;
	export let height: number = 100;

	export let label: string;
	export let svg: string = '';
	export let labelType: 'image' | 'text' = 'text';

	export let inputs: number = 0;
	export let outputs: number = 0;

	export let inputsStore: any = undefined;
	export let outputStore: any = undefined;

	export let inputKeys = [''];
	export let outputKeys = [''];
</script>

<Node
	useDefaults
	{position}
	let:selected
	dimensions={{ width: width, height: height }}
	borderColor="rgb(51,51,51)"
>
	<div class:selected class="node w-full h-full flex p-2">
		<Resizer width height />

		<div class="anchors">
			<div class="input-anchors space-y-1 absolute -left-1">
				{#each { length: inputs } as _, i}
					<Anchor input {inputsStore} key={inputKeys[i]}></Anchor>
				{/each}
			</div>
			<div class="output-anchors space-y-1 absolute -right-1">
				{#each { length: outputs } as _, i}
					<Anchor output {outputStore} key={outputKeys[i]}></Anchor>
				{/each}
			</div>
		</div>

		<div class="label p-1 text-lg m-auto text-center w-full h-full">
			{#if labelType == 'text'}
				<h1 class="">{label}</h1>
				<hr />
			{:else if labelType == 'image'}
				<img src={svg} alt={label} class="w-full h-full object-contain" />
			{/if}

			<div>
				<slot />
			</div>
		</div>
	</div>
</Node>
