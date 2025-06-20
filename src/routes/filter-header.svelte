<script lang="ts" module>
  import type { ComponentProps } from "svelte";

  import * as DropdownMenu from "$lib/components/ui/dropdown-menu";

  import ColumnHeader from "./column-header.svelte";
  import { type ComboProps, default as Combo } from "./combo.svelte";

  export type Props = ComponentProps<typeof ColumnHeader> & {
    combo: ComboProps;
  };
</script>

<script lang="ts">
  const { combo: comboProps, ...restProps }: Props = $props();
</script>

<ColumnHeader label={restProps.label}>
  <DropdownMenu.Sub>
    <DropdownMenu.SubTrigger>Filter</DropdownMenu.SubTrigger>
    <DropdownMenu.SubContent align="start">
      <Combo {...comboProps} />
    </DropdownMenu.SubContent>
  </DropdownMenu.Sub>
</ColumnHeader>
