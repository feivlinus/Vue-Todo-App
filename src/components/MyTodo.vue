<script setup>
import { ref } from 'vue';

const newItem = ref("");

const todoList = ref([
    { id: 1, text: "Steuererklärung machen" },
    { id: 2, text: "Müll runterbringen" },
    { id: 3, text: "Abwasch machen" },
    { id: 4, text: "Vue Tutorials abolvieren" },
    { id: 5, text: "Meditieren" }
]);

function handleSubmit() {
    todoList.value.push({ id: todoList.value.length + 1, text: newItem.value });
    newItem.value = "";
}


</script>

<template>
    <v-container class="mx-auto w-75">
        <v-toolbar :elevation="1" title="This is a Todo List"></v-toolbar>
        <br>
        <v-form @submit.prevent="handleSubmit" class="w-50 my-10" max-width="300px">
            <v-text-field v-model.trim="newItem" placeholder="Add an item..."></v-text-field>
            <v-btn type="submit">Save Item <v-icon icon="mdi-plus-circle"></v-icon></v-btn>
        </v-form>

        <v-card variant="tonal" max-width="300px">
            <v-card-text>{{ newItem }}</v-card-text>
        </v-card>

        <!-- Einfache Liste -->
        <!--     <v-list lines="one">
        <v-list-item v-for="entry in todoList" :key="entry" :title="entry.text"></v-list-item>
    </v-list> -->

        <!-- Card Liste mit Hover-Effekt -->
        <v-card max-width="300">
            <v-list :items="todoList" item-title="text" item-value="text"></v-list>
        </v-card>
    </v-container>
</template>

<style>
.todoList {
    list-style-type: square;
    color: aquamarine;

    :hover {
        color: aqua;
    }
}
</style>