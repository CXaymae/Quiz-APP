<script setup>
// Importing data from quizes.json and necessary Vue functions
import q from "./data/quizes.json";
import { ref, watch } from "vue";

// Importing the Card component
import Card from "./components/Card.vue";

// Creating a ref for the quizes data
const quizes = ref(q);

// Creating a ref for the search input
const search = ref("");

// Watching changes in the search input and filtering quizes accordingly
watch(search, () => {
  quizes.value = q.filter(quiz =>
    quiz.name.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>

<template>
  <div class="container">
    <header>
      <h1>Quizes</h1>
      <!-- Binding the search input to the 'search' ref -->
      <input v-model.trim="search" type="text" placeholder="Search ...">
    </header>
    <div class="options-container"></div>
    <!-- Looping through filtered quizes and rendering the Card component -->
    <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />
    <div class="card">
      <img :src="quiz.img" alt="math">
      <div class="card-text">
        <h2>{{ quiz.name }}</h2>
        <p>{{ quiz.questions.length }} questions</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 1000px;
  margin: 0 auto;
}

header {
  margin-bottom: 10px;
  margin-top: 30px;
  display: flex;
  align-items: center;
}

header h1 {
  font-weight: bold;
  margin-top: 30px;
}

header input {
  border: none;
  background-color: rgba(128, 128, 128, 0.1);
  padding: 10px;
  border-radius: 5px;
}

.options-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 40px;
}

.card {
  width: 310px;
  overflow: hidden;
  border-radius: 2%;
  box-shadow: 1px 1px 1px rgba(0, 0, 0, 0.1);
  margin-bottom: 35px;
  margin-right: 20px;
  cursor: pointer;
}

.card img {
  width: 100%;
  height: 190px;
  margin: 0;
}

.card .card-text {
  padding: 0 5px;
}

.card .card-text h2 {
  font-weight: bold;
}
</style>
