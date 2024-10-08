<script setup>
import { ref, onMounted, computed, watch } from "vue";

const todo = ref([]);
const name = ref("");
const input_content = ref("");
const category = ref(null);

const addTodo = () => {};
const todo_asc = computed(() =>
  todo.value.sort((a, b) => {
    return b.createdAt - a.createdAt;
  }),
);
watch(name, (newVal) => {
  localStorage.setItem("name", newVal);
});

onMounted(() => {
  name.value = localStorage.getItem("name") || "";
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
    <section class="create-todo">
      <h3>Buat ToDo</h3>
      <form @submit.prevent>
        <h4>Apa yang ada dalam dafar "TODO" list Anda?</h4>
        <input
          type="text"
          placeholder="Contoh. Workout"
          v-model="input_content"
        />

        <h4>Pilih Kategori</h4>
        <div class="options">
          <label></label>
        </div>
      </form>
    </section>
  </main>
</template>
