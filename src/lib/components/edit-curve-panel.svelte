<script lang="ts">
	import { createEventDispatcher } from "svelte";
	import EditCurveInput from "./edit-curve-input.svelte";
	import Pencil from "./icons/pencil.svelte";
	import Plus from "./icons/plus.svelte";
	import Trash from "./icons/trash.svelte";
	import MinimalButton from "./minimal-button.svelte";

	const dispatch = createEventDispatcher<{ create: undefined; delete: number }>();

	export let curve: number[];
</script>

<div class="rounded-xl border border-white/10 bg-black text-white shadow-lg">
	<div class="flex items-center justify-between border-b border-white/10 p-3">
		<h3 class="flex items-center gap-1 text-sm">
			<Pencil class="opacity-50" width="15px" height="15px" />
			Edit Curve
		</h3>

		<MinimalButton
			on:click={() => {
				dispatch("create");
			}}
		>
			<Plus />
		</MinimalButton>
	</div>

	<div class="flex w-full items-center gap-2 overflow-auto p-3">
		{#each curve as _, i}
			<div class="flex w-6 flex-col items-center gap-2">
				<input
					class="w-[22px] appearance-none rounded-sm bg-transparent p-0 text-center text-[10px] tabular-nums outline-none ring-white/20 transition-all focus:ring-2"
					bind:value={curve[i]}
				/>
				<EditCurveInput bind:value={curve[i]} />
				<MinimalButton
					disabled={curve.length <= 4}
					on:click={() => {
						dispatch("delete", i);
					}}
				>
					<Trash />
				</MinimalButton>
			</div>
		{/each}
	</div>
</div>
