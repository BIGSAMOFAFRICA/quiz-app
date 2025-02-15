<template>
  <div class="app-container">
    <div class="quiz-wrapper">
      <h1 class="title">Interactive Quiz App</h1>
      <Quiz />
      <DragDrop />
    </div>
  </div>
</template>

<script>
import Quiz from './components/Quiz.vue';
import DragDrop from './components/DragDrop.vue';

export default {
  components: {
    Quiz,
    DragDrop
  }
};
</script>

<style>
/* Global Styles */
body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f7f8fc;
}

.app-container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.quiz-wrapper {
  background-color: #fff;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 800px;
}

.title {
  text-align: center;
  font-size: 32px;
  font-weight: bold;
  margin-bottom: 40px;
  color: #4e73df;
}
</style>
