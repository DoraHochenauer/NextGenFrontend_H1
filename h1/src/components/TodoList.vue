<script setup lang="ts">
import { ref, type Ref } from 'vue'

import todos from './../assets/todos.json'

import ItemComp from '../components/TodoItem.vue'
import type { Item } from '../components/TodoItem.vue'
import { type filterState } from './../TodoApp.vue'

let _itemList: Ref<Item[]> = ref([]);

defineProps<{ filterstate: filterState }>()

function createItem(id: number, header: string, content: string, state: boolean): Item {
    return { id: id, header: header, content: content, done: state };
}

function AddItem(item: Item) {
    _itemList.value.push(item);
}

//IMPORT JSON
console.log(todos);
todos.forEach((todo) => {
    AddItem(createItem(todo.id, todo.header, todo.content, todo.done));
})



//'leider' emit nicht notwendig weil v-if reagiert
/*
function CheckChange() {
    console.log('CHECK CHANGED');
}
*/




function DeleteItem(id: number) {
    RemoveItem(id);
}

function RemoveItem(id: number) {
    const index = _itemList.value.findIndex(function (item) {
        return item.id === id
    })

    _itemList.value.splice(index, 1);

}


</script>

<template>
    
    <ul class="item-list" v-for="item in _itemList">
        <ItemComp @delete-item="DeleteItem(item.id)"
            v-if="filterstate == 'all' || filterstate == 'open' && item.done == false || filterstate == 'closed' && item.done == true"
            :item="item" />
    </ul>

</template>
