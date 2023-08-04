<template>
  <div class="overflow-auto full-width">
    <table class="reportTable full-width q-border-small q-border-collapse-col">
      <thead class="bg-accent text-grey-1">
      <tr>
        <th
          class="q-border-small q-pa-md"
          v-for="column in selectedReport.header"
          :key="column.id"
        >{{ column.caption }}
        </th>
      </tr>
      </thead>

      <tbody>
      <tr v-for="(row, index) in selectedReport.data" :key="index">
        <td
          v-for="(column, i) in selectedReport.header"
          :key="column.id"
          class="q-pa-md q-border-small"
          :style="{ textAlign: column.align ? column.align : getAlignPosition(column.type) }"
        >{{ cellData(row[i]) }}
        </td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script lang="ts">
import {defineComponent} from 'vue';

export default defineComponent({
  name: 'ReportsTable',
  props: ['selectedReport'],
  methods: {
    getAlignPosition(type: string): string {
      switch (type) {
        case 'string':
          return 'left';
        case 'boolean':
          return 'center';
        case 'float':
        case 'number':
          return 'right'
        default:
          return 'left';
      }
    },
    cellData(value: { d: string } | boolean | string | number) {
      if (typeof value === 'object') {
        return value.d;
      } else if (typeof value === 'boolean') {
        return value ? 'Отправлено' : 'Не отправлено';
      } else {
        return value;
      }
    },
  },
});
</script>

