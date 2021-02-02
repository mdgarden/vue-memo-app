<template>
  <div class="memo-app">
      <memo-form />
      <memo />
  </div>
</template>

<script>
import MemoForm from './MemoForm';
import Memo from './Memo';

export default {
    name: 'MemoApp',//컴포넌트 이름
    components: {
      MemoForm,
      Memo
    }, 
    data(){
      return {
        memos:[],
      };
    },
  created(){
  // 1. 만약긱존에 추가된 local storage에 데이터가 있다면 created 훅에서 localStorage의 데이터를
  //컴포넌트 내의 memos 데이터에 넣어주고, 그렇지 않다면 그대로 빈 배열로 초기와
    this.memos = localStorage.memos ? JSON.parse(localStorage.memos):[];
  }
}
</script>

<style scoped>

</style>