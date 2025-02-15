<template>
  <div class="drag-and-drop-container">
    <h2>Drag and Drop: Match the Capitals</h2>
    <div class="drag-container">
      <div
        v-for="(capital, index) in capitals"
        :key="index"
        class="drag-item"
        draggable="true"
        @dragstart="dragStart(index)"
      >
        {{ capital }}
      </div>
    </div>
    <div class="drop-container">
      <div
        v-for="(country, index) in countries"
        :key="index"
        class="drop-zone"
        @dragover.prevent
        @drop="drop(index)"
      >
        {{ country }}
      </div>
    </div>
    <p v-if="dropFeedback" :class="dropFeedbackClass">{{ dropFeedback }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      capitals: ['Paris', 'Berlin', 'Madrid', 'Rome'],
      countries: ['France', 'Germany', 'Spain', 'Italy'],
      draggedItem: null,
      dropFeedback: '',
      dropFeedbackClass: '',
    };
  },
  methods: {
    dragStart(index) {
      this.draggedItem = index;
    },
    drop(index) {
      const temp = this.capitals[this.draggedItem];
      this.capitals[this.draggedItem] = this.capitals[index];
      this.capitals[index] = temp;

      // Check if capitals match with countries
      if (this.capitals[index] === this.countries[index]) {
        this.dropFeedback = 'Correct match!';
        this.dropFeedbackClass = 'correct';
      } else {
        this.dropFeedback = 'Incorrect match. Try again!';
        this.dropFeedbackClass = 'wrong';
      }
    },
  },
};
</script>

<style scoped>
.drag-and-drop-container {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 400px;
  margin: 0 auto;
}

.drag-container {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.drag-item {
  background-color: #007bff;
  color: #fff;
  padding: 10px;
  border-radius: 4px;
  cursor: pointer;
}

.drop-container {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.drop-zone {
  background-color: #f0f0f0;
  padding: 15px;
  border-radius: 4px;
  border: 2px dashed #ccc;
  text-align: center;
}

.correct {
  color: green;
}

.wrong {
  color: red;
}
</style>
