<script lang="ts">
  import FilterHeader from "./filter-header.svelte";
  import ColumnHeader from "./column-header.svelte";
  import Combo from "./combo.svelte";

  import * as DropdownMenu from "$lib/components/ui/dropdown-menu";

  let value = $state("");

  const onChange = (v: string) => (value = v);
</script>

<div class="m-8 flex flex-col gap-8">
  <pre>"value": "{value}"</pre>
  <div class="flex gap-8">
    <FilterHeader
      label="Problematic"
      combo={{
        value,
        items: [
          { value: "1", label: "1" },
          { value: "2", label: "2" },
        ],
        onChange,
        placeholder: "Search...",
        empty: "Nothing found.",
      }}
    />
    <ColumnHeader label="Works Fine">
      <DropdownMenu.Sub>
        <DropdownMenu.SubTrigger>Filter</DropdownMenu.SubTrigger>
        <DropdownMenu.SubContent align="start">
          <Combo
            {value}
            items={[
              { value: "1", label: "1" },
              { value: "2", label: "2" },
            ]}
            {onChange}
            placeholder="Search..."
            empty="Nothing found."
          />
        </DropdownMenu.SubContent>
      </DropdownMenu.Sub>
    </ColumnHeader>
  </div>
</div>
