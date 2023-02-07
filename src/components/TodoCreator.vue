<template>
  <div class="input-wrap" :class="{'input-err': invalid}">
    <input type="text" v-model="todo" />
    <todo-button @click="createTodo()">Create</todo-button>
  </div>
  <p v-show="invalid" class="err-msg">{{ errMsg }}</p>
</template>

<script setup>
import { ref } from "@vue/reactivity";
import TodoButton from './TodoButton.vue'

const todo = ref("");
const invalid = ref(null);
const errMsg = ref("");

const emit = defineEmits(["create-todo"]);

const createTodo = () => {
  invalid.value = null;
  if (todo.value !== "") {
    emit("create-todo", todo.value);
    todo.value = "";
    return;
  }
  invalid.value = true;
  errMsg.value = "Todo value cannot be empty";
};
</script>

<style lang="scss" scoped>
.input-wrap {
  display: flex;
  transition: 250ms ease;
  border: 2px solid #41b080;
  &.input-err {
    border-color: red;
  }
  &:focus-within {
    box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1),
      0 -2px 4px -2px rgb(0 0 0 / 0.1);
  }
  input {
    width: 100%;
    padding: 8px 6px;
    border: none;
    &:focus {
      outline: none;
    }
  }
}
.err-msg {
  margin-top: 6px;
  font-size: 12px;
  text-align: center;
  color: red;
}
</style>
