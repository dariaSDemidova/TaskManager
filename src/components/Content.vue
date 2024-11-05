<script>
export default {
  data() {
    return {
      task: '',
      listTask: [],
      selectedTask: null
    };
  },
  methods: {
    addTask() {
      if (this.task.trim()) {
        this.listTask.push(this.task.trim());
        this.task = '';
      }
    },
    sortTask() {
      this.listTask.sort();
    },
    deleteTask() {
      if (this.selectedTask !== null) {
        this.listTask.splice(this.selectedTask, 1);
        this.selectedTask = null;
      }
    }
  }
};
</script>

<template>
  <div class="content">
    <div class="container">
      <p>Тут добавляй задачи</p>
      <div class="task-add">
        <input class="input" type="text" v-model="task" placeholder="Введите задачу...">
        <button class="add-button" @click="addTask">Добавить</button>
      </div>
      <p>Тут смотри задачи</p>
      <ul>
        <li class="task-item" v-for="(item, index) in listTask" :key="index">
          <input type="radio" name="task" :value="index" v-model="selectedTask" />
          {{ item }}
        </li>
      </ul>
      <div class="actions">
        <button class="button" @click="sortTask">Сортировать</button>
        <button class="button" @click="deleteTask">Удалить</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .container {
    width: 80%;
    background-color: #9DA3A4;
    border-radius: 10px;
    padding: 25px;
    margin: 70px auto;
  }

  .container p {
    font-size: 25px;
    text-transform: uppercase;
    color: #604D53;
    margin: 10px 0;
  }

  .task-add {
    display: flex;
    align-items: center;
  }

  .input {
    width: 80%;
    height: 40px;
    border: none;
    margin: 10px 0;
    border-radius: 5px;
    outline: none;
    margin-right: 10px;
    padding: 0 10px;
    color: #604D53;
    font-size: 16px;
  }

  .add-button {
    width: 250px;
    height: 40px;
    border: none;
    margin-top: 10px 0;
    background-color: #FFDBDA;
    color: #604D53;
    font-size: 20px;
    font-weight: bold;
    text-transform: uppercase;
    border-radius: 5px;
    cursor: pointer;
  }

  .task-item {
    color: #604D53;
    padding: 5px 0;
    display: flex;
    align-items: center;
  }
  
  .button {
    background-color: #FFDBDA;
    color: #604D53;
    border: none;
    border-radius: 5px;
    width: 250px;
    height: 35px;
    margin: 10px 1%;
    font-size: 14px;
    font-weight: bold;
    text-transform: uppercase;
    cursor: pointer;
  }

  input[type="radio"] {
  appearance: none;
  background: #FFFFFF;
  border: 2px solid #604D53;
  height: 1.5em;
  width: 1.5em;
  margin: 0 10px;
  border-radius: 100%;
  position: relative;
}

input[type="radio"]::before {
  content: "";
  position: absolute;
  margin: auto;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
}

input[type="radio"]:checked::before {
  border: 4px solid transparent;
  border-radius: 100%;
  background-color: #604D53;
  margin: 1px;
}
</style>