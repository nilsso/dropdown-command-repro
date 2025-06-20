<script lang="ts" module>
  import type { ComponentProps } from "svelte";

  import CheckIcon from "@lucide/svelte/icons/check";

  import { cn } from "$lib/utils";

  import * as Command from "$lib/components/ui/command";

  export type ComboProps = {
    value: string;
    items: {
      value: string;
      label: string;
    }[];
    onChange?: (value: string) => void;
    placeholder?: string;
    empty?: string;
  };

  export type Props = ComponentProps<typeof Command.Root> & ComboProps;
</script>

<script lang="ts">
  const {
    value: currentValue,
    items,
    onChange,
    placeholder = "Search...",
    empty = "None found.",
    ...restProps
  }: Props = $props();
</script>

<Command.Root {...restProps}>
  <Command.Input {placeholder} />
  <Command.List>
    <Command.Empty>{empty}</Command.Empty>
    <Command.Item onSelect={() => onChange?.("")}>
      <CheckIcon class={cn(!!currentValue && "text-transparent")} /> Any
    </Command.Item>
    {#each items as { value, label } (label)}
      <Command.Item {value} onSelect={() => onChange?.(value)}>
        <CheckIcon class={cn(value !== currentValue && "text-transparent")} />
        {label}
      </Command.Item>
    {/each}
  </Command.List>
</Command.Root>
