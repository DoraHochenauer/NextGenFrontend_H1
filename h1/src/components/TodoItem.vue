<script setup lang="ts">


export interface Item {
    id: number
    header: string
    content: string
    done: boolean
}


// gibt Item an Parent (Liste)
defineProps<{ item: Item }>()

//emit damit Liste auf checkbox Änderung reagiert = nicht notwendig weil v-if auf item done reagiert
//const emit = defineEmits(['checkChange']);

//emittet delete an Parent Liste
const emit = defineEmits(['deleteItem']);



</script>

<template>
    <div class="item" :class="{ done: item.done }">

        <div class="item-text">

            <h2>{{ item.header }}</h2>
            <p>{{ item.content }}</p>
        </div>

        <div class="item-controls">
            <span class="checkbox">
                <input type="checkbox" id="checkbox" v-model="item.done" />
            </span>
            <button class="delete-button todo-button" @click="$emit('deleteItem', item.id)">Löschen</button>
        </div>
    </div>


</template>
