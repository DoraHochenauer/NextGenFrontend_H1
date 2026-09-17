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
    <h1>To Do App</h1>
    <p>Filter: {{ filterstate }}</p>
    <p>Toggle Filter</p>
    <button  class="filter-button todo-button"  @click="ChangeFilter('open')">open</button>
    <button  class="filter-button todo-button"  @click="ChangeFilter('closed')">closed</button>
    <button  class="filter-button todo-button"  @click="ChangeFilter('all')">all</button>
  </div>
  <div>
    <List :filterstate=filterstate />
  </div>


</template>
