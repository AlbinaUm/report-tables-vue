<template>
  <q-layout view="lHh Lpr lFf">
    <q-header reveal :class="$q.dark.isActive ? 'bg-secondary' : 'bg-black'">
      <div class="q-page-container">
        <q-toolbar>
          <router-link
            to="/"
            class="text-grey-1 logo"
          ><q-toolbar-title>Report Table</q-toolbar-title></router-link>
        </q-toolbar>
      </div>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'MainLayout',
});
</script>
