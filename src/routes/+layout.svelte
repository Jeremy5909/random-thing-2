<script lang="ts">
	import '../app.pcss';
	import { Svelvet } from 'svelvet';

	import MathNode from '../Nodes/MathNode.svelte';
	import Number from '../Nodes/Number.svelte';
	import Viewer from '../Nodes/Viewer.svelte';
</script>

<body class="flex justify-center items-center bg-gray-500 w-screen h-screen p-0 m-0">
	<Svelvet minimap theme="dark" zoom={0.8}>
		<Number position={{ x: 40, y: 200 }} />
		<Number position={{ x: 40, y: 400 }} />
		<MathNode position={{ x: 350, y: 300 }} />
		<Viewer position={{ x: 700, y: 300 }} />
	</Svelvet>
</body>
