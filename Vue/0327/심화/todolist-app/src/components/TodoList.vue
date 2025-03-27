<template lang="">
  <div class="row">
    <div class="col">
      <ul class="list-group">
        <TodoListItem
          v-for="todo in todolist"
          :todoItem="todo"
          @delete-todo="emit('delete-todo', todo.id)"
          @toggle-completed="$emit('toggle-completed', todo.id)"
        />
      </ul>
    </div>
  </div>
</template>

<script setup>
import TodoListItem from './TodoListItem.vue';

const props = defineProps({
  todolist: { type: Array, required: true },
});

const emit = defineEmits(['delete-todo', 'toggle-completed']);

// import TodoListItem from './TodoListItem.vue';

// export default {
//   name: 'TodoList',
//   components: { TodoListItem },
//   //부모로 부터 전달받은 데이터를 수신 + 유효성 검사
//   props: {
//     todolist: { type: Array, required: true },
//   },

//   //부모 컴포넌트로 방출되는 이벤트 검사
//   emits: ['toggle-completed', 'delete-todo'],
// };
</script>
