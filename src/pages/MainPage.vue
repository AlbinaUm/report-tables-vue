<template>
  <q-page>
    <CustomSelect
      v-if="data.length > 0"
      :data="data"
      :selected-report="selectedReport"
      @selectChanged="handleSelectChange"
    />

    <ReportsTable v-if="data.length > 0" :selectedReport="selectedReport"/>

    <q-card v-if="data.length < 0 || !data">
      <q-card-section class="text-center q-ma-md">
        На данный момент, данных нет
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script lang="ts">
import ReportsTable from 'components/ReportsTable/ReportsTable.vue';
import CustomSelect from 'components/UI/CustomSelector/CustomSelector.vue';
import {data} from 'src/config/constants';
import {defineComponent} from 'vue';

export default defineComponent({
  name: 'MainPage',
  components: {CustomSelect, ReportsTable},
  data: () => ({
    data: data,
    selectedReport: data.length > 0 ? data[0].data : null,
  }),
  methods: {
    handleSelectChange(value: number) {
      this.selectedReport = data[value].data;
    },
  },
});
</script>
