<script setup>
import { ref, onMounted, computed, watch } from "vue";

const todo = ref([]);
const name = ref("");
const input_content = ref("");
const category = ref(null);

const todo_asc = computed(() =>
  todo.value.sort((a, b) => {
    return b.createdAt - a.createdAt;
  }),
);
watch(name, (newVal) => {
  localStorage.setItem("name", newVal);
});
</script>

<template>
  <main class="app">
    <section class="greetings">
      <h2 class="tittle">
        Halo Apakabar?
        <input type="text" placeholder="Nama Di sini" v-model="name" />
      </h2>
    </section>
  </main>
</template>
