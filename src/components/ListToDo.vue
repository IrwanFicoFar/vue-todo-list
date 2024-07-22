<template>
  <div class="child">
    <div v-for="toDo in todos" :key="toDo.id" class="parent-list">
      <div class="todo-list" :class="{ 'is-done': toDo.isDone }">
        <input
          class="form-check-input"
          type="checkbox"
          :id="'todo-' + toDo.id"
          v-model="toDo.isDone"
          @change="updateToDoStatus(toDo)"
        />
        <label :for="'todo-' + toDo.id">{{ toDo.name }}</label>
      </div>
      <button @click="confirmDelete(toDo.id)" class="btn btn-danger">
        Delete
      </button>
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap/dist/js/bootstrap.bundle.min.js";

export default {
  name: "ListToDo",
  props: {
    todos: {
      type: Array,
      required: true,
    },
  },
  methods: {
    updateToDoStatus(toDo) {
      this.$emit("todo-updated", toDo);
    },
    confirmDelete(id) {
      if (window.confirm("Are you sure you want to delete this item?")) {
        this.deleteTodo(id);
      }
    },
    deleteTodo(nId) {
      this.$emit("todo-deleted", nId);
    },
  },
};
</script>

<style scoped lang="scss">
.todo-list {
  /* color: black; */
  font-size: larger;
  background-image: linear-gradient(
    rgba(216, 49, 49, 0.1),
    rgba(170, 170, 170, 0.3),
    rgba(112, 112, 112, 0.4)
  );
  border-radius: 0.5em;
  display: flex;
  gap: 1em;
  align-items: center;
  padding: 0.5em 1em 0.5em 1em;
}

.child {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 2em 2em 2em 2em;
}

.parent-list {
  display: flex;
  gap: 0.5em;

  &:hover {
    scale: 1.02;
    transform: translateX(0.5em);
    animation-duration: 5s;
    animation-delay: 0.2;
    cursor: pointer;
  }
}

.is-done {
  color: white;
  background-color: darkcyan;
  text-decoration: line-through;
}

.btn-danger {
  border-radius: 1em;
}
</style>
