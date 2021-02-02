<template>
  <div class="memo-form">
    <form>
      <fieldset>
      <div>
        <input class="memo-form__title-form" type="text" placeholder="메모의 제목을 입력해주세요" />
        <textarea class="memo-form__content-form" placeholder="메모의 내용을 입력해주세요." />
        <button type="reset"><i class="fas fa-sync-alt"></i></button>
      </div>
      <button type="submit">등록하기</button>
      </fieldset>
    </form>
  </div>
</template>

<script>
export default {
    name: 'MemoForm'
}
</script>

<style scoped>
    .memo-form{
      margin-bottom: 24px;
      padding-bottom: 40px;
      border-bottom: 1px solid #eee;
    }
    
    .memo-form form fieldset div {
      position: relative;
      padding: 24px;
      margin-bottom: 20px;
      box-shadow: 0 4px 10px -4px rgba(0, 0, 0, 0.2);
      background-color: #ffffff;
    }

    .memo-form form fieldset div button[type="reset"] {
      position: absolute;
      right: 20px;
      bottom: 20px;
      font-size: 16px;
      background: none;
    }

    .memo-form form fieldset button[type="submit"] {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
      float: right;
      width: 96px;
      padding: 12px 0;
      border-radius: 4px;
      background-color: #ff5a00;
      box-shadow: 0 4px 10px -4px rgba(0, 0, 0, 0.2);
      color: #fff;
      font-size: 16px;
      font-weight: 600;
    }

    .memo-form form fieldset .memo-form__title-form {
      width: 100%;
      margin-bottom: 12px;
      font-size: 18px;
      line-height: 26px;
    }

    .memo-form form fieldset .memo-form__content-form {
      width: 100%;
      height: 66px;
      font-size: 14px;
      line-height: 22px;
      vertical-align: top;
    }

    .memo-form input:focus {
      outline: none;
    }

    .memo-form textarea:focus {
      outline: none;
    }

    .memo-form textarea {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    }
</style>