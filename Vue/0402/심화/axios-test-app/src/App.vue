<template>
  <div>
    <h2>콘솔을 확인합니다.</h2>
  </div>
</template>
<script setup>
import axios from 'axios';

// -------------------1번-------------------
//  const requestAPI = () => {
//   const url = '/api/todos/1';
//   axios.get(url).then((response) => {
//     console.log('# 응답객체 : ', response.data);
//   });
// };

//requestAPI();

// -------------------2번-------------------
const requestAPI = () => {
  let todoList = [];
  const url = '/api/todos/';
  axios
    .get(url)
    .then((response) => {
      todoList = response.data;

      console.log('# TodoList : ', todoList);
      return todoList[0].id;
    })
    .then((id) => {
      return axios.get(url + id);
    })
    .then((response) => {
      console.log('## 첫번째 Todo : ', response.data);
      return todoList[1].id;
    })
    .then((id) => {
      axios.get(url + id).then((response) => {
        console.log('## 두번째 Todo : ', response.data);
      });
    });
};

requestAPI();
</script>
