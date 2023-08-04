<template>
  <select @change="handleChange" class="q-my-md q-px-md q-py-sm">
    <option disabled value="null">Select the option</option>
    <option v-for="(d, index) in data" v-bind:value="index" :key="d.id">
      {{ d.name }}
    </option>
  </select>
</template>

<script lang="ts">
import { defineComponent } from 'vue';


export default defineComponent({
  name: 'CustomSelect',
  props: ['data', 'selectedReport'],
  methods: {
    handleChange(event:  Event) {
      const selectedValue = (event.target as HTMLSelectElement).value;
      this.$emit('selectChanged', selectedValue);
    },
  },
});
</script>
