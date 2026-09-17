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
    <span class="item">

        <h2>{{ item.header }}</h2>
        <span>{{ item.content }}</span>
        <input type="checkbox" id="checkbox" v-model="item.done" />
        <button @click="$emit('deleteItem', item.id)">delete</button>
    </span>


</template>
