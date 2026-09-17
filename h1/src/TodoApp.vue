<script setup lang="ts">
import List from './components/TodoList.vue'
import { ref, type Ref } from 'vue'

export type filterState = 'open' | 'closed' | 'all';

let filterstate: Ref<filterState> = ref('open');

function ChangeFilter(newfilterState: filterState) {
    filterstate.value = newfilterState;
    console.log(filterstate);
}

</script>

<template>
  <div>
    <List :filterstate=filterstate />
  </div>

  <div>
        <p>Filter: {{ filterstate }}</p>
        <p>Toggle Filter</p>
        <button @click="ChangeFilter('open')">open</button>
        <button @click="ChangeFilter('closed')">closed</button>
        <button @click="ChangeFilter('all')">all</button>
    </div>

</template>
