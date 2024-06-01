<script>
	import "../app.pcss";

	import Toast from "$lib/components/toast.svelte";
	import { Toaster } from "$lib/components/ui/sonner";
	import Metadata from "$lib/components/metadata.svelte";
</script>

<svelte:head>
	<title>Coco Palette Generator</title>
</svelte:head>

<Metadata />
<Toaster />

<slot />
