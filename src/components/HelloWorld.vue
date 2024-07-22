<template>
  <div class="hello container">
    <h1>{{ msg }}</h1>

    <div class="row parent">
      <div class="col">
        <h2>What to do ?</h2>
        <div class="child">
          <ListToDo
            :todos="results"
            @todo-updated="handleTodoUpdate"
            @todo-deleted="handleDeletedTodo"
          />
        </div>
      </div>
    </div>
    <div class="parent-add-new">
      <div class="row add-new" v-if="!showAddForm">
        <div class="col">
          <button @click="toggleAddForm" class="btn">Add New</button>
        </div>
      </div>
      <div class="row add-new" v-if="showAddForm">
        <div class="col">
          <input
            v-model="newToDo"
            placeholder="Enter new to-do item"
            class="form"
          />
        </div>
        <div class="col d-flex gap-2">
          <button @click="toggleAddForm" class="btn btn-cancel">Cancel</button>
          <button @click="saveToDo" class="btn btn-save">Save</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ListToDo from "./ListToDo.vue";

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data: function () {
    return {
      showAddForm: false,
      newToDo: "",
      results: [
        {
          id: 1,
          name: "cuci baju",
          isDone: false,
        },
        {
          id: 2,
          name: "belajar bahasa inggris",
          isDone: true,
        },
        {
          id: 3,
          name: "berdoa",
          isDone: false,
        },
      ],
    };
  },
  components: {
    ListToDo,
  },
  methods: {
    toggleAddForm() {
      this.showAddForm = !this.showAddForm;
    },
    saveToDo() {
      if (this.newToDo.trim()) {
        this.results.push({
          id: this.results.length + 1,
          name: this.newToDo,
          isDone: false,
        });
        this.newToDo = "";
        this.showAddForm = false;
      }
    },
    handleDeletedTodo(nId) {
      this.results = this.results.filter((toDo) => toDo.id !== nId);
    },
  },
};
</script>

<style lang="scss" scoped>
h2 {
  background-color: darkcyan;
  border-radius: 0.7em;
  color: aqua;
  padding: 0.5em 0em 0.5em 0em;
  margin-top: 0.4em;
}

.parent {
  background-color: aquamarine;
  margin-top: 2em;
  border-radius: 2em;
  box-shadow: 0.5em 0.5em;

  &:hover {
    background-color: aquamarine;
    margin-top: 2em;
    border-radius: 2em;
    box-shadow: 0.5em 0.5em;
    transform: scale(1.01);
    animation-duration: 1s;
    animation-delay: 0.2s;
    cursor: pointer;
  }
}

.parent-add-new {
  display: flex;
  justify-content: end;
  margin: 2em 0em 1em 0em;
}

.add-new {
  @extend .parent;
  padding: 0.5em 0.2em 0.5em 0.2em;
  display: flex;
  align-items: center;
}

.add-new h3 {
  @extend h2;
  padding: 0em 1em 0em 1em;
}

.form {
  outline: none;
  border: none;
  border-radius: 0.5em;
  padding: 0.2em 0.5em 0.2em 0.5em;
}

.btn-save {
  background-color: darkcyan;
  border-radius: 1em;
  color: white;
  font-weight: 500;

  &:hover {
    background-color: darkcyan;
    color: white;
    scale: 102%;
  }
}

.btn-cancel {
  @extend .btn-save;
  background-color: orange;

  &:hover {
    background-color: orange;
    scale: 102%;
  }
}
</style>
