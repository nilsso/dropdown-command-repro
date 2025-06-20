<script lang="ts" module>
  import type { ComponentProps } from "svelte";

  import ChevronsUpDownIcon from "@lucide/svelte/icons/chevrons-up-down";

  import Button from "$lib/components/ui/button/button.svelte";
  import * as DropdownMenu from "$lib/components/ui/dropdown-menu";

  export type Props = ComponentProps<typeof DropdownMenu.Root> & {
    label: string;
  };
</script>

<script lang="ts">
  let { label, children, ...restProps }: Props = $props();
</script>

<DropdownMenu.Root {...restProps}>
  <DropdownMenu.Trigger>
    {#snippet child({ props })}
      <Button {...props} variant="outline" class="data-[state=open]:bg-accent">
        <span>{label}</span>
        <ChevronsUpDownIcon />
      </Button>
    {/snippet}
  </DropdownMenu.Trigger>
  <DropdownMenu.Content>
    {@render children?.()}
  </DropdownMenu.Content>
</DropdownMenu.Root>
