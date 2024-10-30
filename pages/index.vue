<script setup lang="ts">
import type { ActiveStock } from "~/utils/type";

const fetchData = async (): Promise<ActiveStock[]> => {
  const data = await $fetch<ActiveStock[]>(
    "https://financialmodelingprep.com/api/v3/stock_market/actives?apikey=Ai7NmAPUE7MqHIsSWf4dgsoSvOa658He"
  );

  console.log(data);
  return data.slice(0, 10);
};

const activeStocks = ref<ActiveStock[]>([]);
onMounted(async () => {
  activeStocks.value = await fetchData();
});
</script>

<template>
  <div class="">
    <DataTable
      :value="activeStocks"
      striped-rows
      table-style="width: 50px"
      size="small"
      class="text-xs"
    >
      <Column field="symbol" header="Symbol" />
      <Column field="name" header="Name" />
      <Column field="change" header="Change" />
      <Column field="price" header="Price" />
      <Column field="changesPercentage" header="Changes Percentage" />
    </DataTable>
  </div>
</template>
