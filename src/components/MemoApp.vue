<template>
  <div class="memo-app">
      <memo-form @addMemo="addMemo"/>
      <ul class="memo-list">
        <memo v-for="memo in memos" :key="memo.id" :memo="memo" @deleteMemo="deleteMemo" @updateMemo="updateMemo"/>
      </ul>
  </div>
</template>

<script>
import axios from 'axios';
import MemoForm from './MemoForm';
import Memo from './Memo';

const memoAPIcore = axios.create({
  baseURL: 'http://localhost:3000/memos'
});

export default {
  name: 'MemoApp',//컴포넌트 이름
  data(){
    return {
      memos:[],
    };
  },
    methods: {
      addMemo(payload) {
        memoAPIcore.post('/', payload).then(res => {
          this.memos.push(res.data);
        });
      },
      storeMemo() {
        const memoToString = JSON.stringify(this.memos);
        localStorage.setItem('memos', memoToString);
      },
      deleteMemo(id) {
        const targetIndex = this.memos.findIndex(v => v.id === id);
        this.memos.splice(targetIndex, 1);
        this.storeMemo();
      },
      updateMemo(payload) {
        const { id, content } = payload;
        const targetIndex = this.memos.findIndex(v => v.id === id);
        const targetMemo = this.memos[targetIndex];
        this.memos.splice(targetIndex, 1, { ...targetMemo, content });
        this.storeMemo();
      },
      created() {
        memoAPIcore.get('/').then(res => {
          this.memos = res.data;
        });
      }
    },
    components: {
      MemoForm,
      Memo
    }, 
  created(){
  // 1. 만약긱존에 추가된 local storage에 데이터가 있다면 created 훅에서 localStorage의 데이터를
  //컴포넌트 내의 memos 데이터에 넣어주고, 그렇지 않다면 그대로 빈 배열로 초기와
    this.memos = localStorage.memos ? JSON.parse(localStorage.memos):[];
  }
}
</script>

<style scoped>
  .memo-list {
    padding: 20px 0;
    margin: 0;
  }
</style>