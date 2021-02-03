<template>
  <div class="memo-app">
      <memo-form @addMemo="addMemo"/>
      <memo />
  </div>
</template>

<script>
import MemoForm from './MemoForm';
import Memo from './Memo';

export default {
    name: 'MemoApp',//컴포넌트 이름
    methods: {
      addMemo(payload) {
        //Memoform 에서 올려 받은 데이터를 먼저 컴포넌트 내부 뎅터에 추가
        this.memos.push(payload);
        //내부 데이터를 문자열로 변환 후 로컬 스토리지에 저장
        this.storeMemo();
      },
      storeMemo() {
        const memoToString = JSON.stringify(this.memos);
        localStorage.setItem('memos', memoToString);
      }
    },
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