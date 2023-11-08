<script setup>
import { ref } from 'vue'

const newItem = ref('')

//Mockup todo list
/* const todoList = ref([
    { id: 1, text: "Steuererklärung machen" },
    { id: 2, text: "Müll runterbringen" },
    { id: 3, text: "Abwasch machen" },
    { id: 4, text: "Vue Tutorials abolvieren" },
    { id: 5, text: "Meditieren" }
]); */

//Empty List
const todoList = ref([])

function handleSubmit() {
  todoList.value.push({ id: todoList.value.length + 1, text: newItem.value })
  newItem.value = ''
}
</script>

<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <v-card color="light-blue-darken-3">
          <v-row>
            <v-col cols="12"><v-card-title>My Todo List App</v-card-title></v-col>

            <v-card-text>
              <!-- Formular -->
              <v-col cols="12" justify="center">
                <v-form @submit.prevent="handleSubmit">
                  <v-text-field
                    v-model.trim="newItem"
                    placeholder="Add something to do..."
                  ></v-text-field>
                  <v-btn type="submit" color="light-blue-darken-4"
                    >Save Item <v-icon icon="mdi-plus-circle"></v-icon
                  ></v-btn>
                </v-form>
              </v-col>
              <!--
            <v-card variant="tonal" max-width="300px">
                <v-card-text>{{ newItem }}</v-card-text>
            </v-card> 
            -->

              <!-- Einfache Liste -->
              <!--     
            <v-list lines="one">
                <v-list-item v-for="entry in todoList" :key="entry" :title="entry.text"></v-list-item>
            </v-list> 
            -->

              <!-- Card Liste mit Hover-Effekt -->
              <v-col cols="12" align-self="center">
                <v-card color="light-blue-darken-1" v-if="todoList.length !== 0">
                  <v-list
                    :items="todoList"
                    item-title="text"
                    item-value="text"
                    class="text-center"
                    bg-color="light-blue-darken-2"
                  ></v-list>
                </v-card>
              </v-col>
            </v-card-text>
          </v-row>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<style>
body {
  background-color: #01579b;
}
h1 {
  text-align: center;
}
.todoList {
  color: aquamarine;
  :hover {
    color: aqua;
  }
}
</style>
