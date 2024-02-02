<script lang="ts">
	import * as Select from "@/registry/default/ui/select";
	import { getFormField } from "formsnap";
	import type { Select as SelectPrimitive } from "bits-ui";

	type $$Props = SelectPrimitive.Props<unknown>;
	const { setValue, name, value } = getFormField();
	export let onSelectedChange: $$Props["onSelectedChange"] = undefined;
	export let selected = { value: $value, label: $value.charAt(0).toUpperCase() + $value.slice(1) }
</script>

<Select.Root
	onSelectedChange={(v) => {
		onSelectedChange?.(v);
		setValue(v ? v.value : undefined);
	}}
	bind:selected
	{...$$restProps}
>
	<slot />
	<input hidden {name} value={$value} />
</Select.Root>
