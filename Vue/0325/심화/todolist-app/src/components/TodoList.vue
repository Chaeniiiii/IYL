<template lang="">
<div class="row">
    <div class="col">
        <ul class="list-group">

            <!-- <p v-for="todo in todolist">{{todo}}</p> -->

            <!-- 할 일 목록 요소 컴포넌트 -->

            <!-- props로 받은 데이터 수정 X 
                -> emit을 이용해서 부모로 전달하여 수정
                TodoItem -> TodoList -> App 
            -->
            <TodoListItem
                v-for="todo in todolist"
                :todoItem="todo"
                @toggle-completed="$emit('toggle-completed',$event)"
                @delete-todo="$emit('delete-todo',$event)"
            />
            <!-- 
                $event : 자식 컴포넌트에서 방출된 payload 참조 변수 (=id)
            -->

        </ul>
    </div>
</div>
</template>

<script>

import TodoListItem from './TodoListItem.vue'

export default {
    name : 'TodoList',
    components : {TodoListItem},
    //부모로 부터 전달받은 데이터를 수신 + 유효성 검사
    props : {
        todolist : {type : Array, required : true},
    },

    //부모 컴포넌트로 방출되는 이벤트 검사 
    emits: ['toggle-completed','delete-todo']
};
</script>