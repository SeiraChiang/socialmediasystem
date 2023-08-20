<script setup lang="ts">
import { ref } from 'vue';
// import ArticleContent from './components/ArticleContent.vue';


interface articleData {
  text: string;
  // completed: boolean;
  // date: string;
  // time: string;
}

const newarticleData = ref<articleData>({
  text: '',
  // completed: false,
  // date: '',
  // time: ''
});
const articleDatas = ref<articleData[]>([]);

const addArticle = () => {
  if (newarticleData.value.text.trim() !== '') {
    articleDatas.value.push({ ...newarticleData.value });
    newarticleData.value = { text: '' };
  }
};

const deleteArticle = (index: number) => {
  articleDatas.value.splice(index, 1);
};

const handleInputKeydown = (event: KeyboardEvent) => {
  if (event.key === 'Enter') {
    addArticle();
  }
};

</script>

<template>
  <div>

    <div class="register">
      <h2>登入</h2>
      <form action="" method="post">
        <p>手機號碼：</p>
        <input type="number" placeholder="請輸入手機號碼" />
        <p>密碼：</p>
        <input type="password" placeholder="請輸入密碼" />

        <button>登入</button>

        <a href="register.html">
          <button>註冊帳號</button>
        </a>
      </form>
    </div>


  </div>
</template>

<style scoped>
/* 發文頁面 */


/* 註冊功能 */
.register {
  margin-bottom: 10px;
  border: 1px solid #213547;
  padding: 20px;
  border-radius: 5px;
}

form {
  /* display: flex; */
  width: 300px;
  margin: 20px;
}

form p {
  text-align: left;
}

form button {
  margin-top: 20px;
  margin-right: 20px;
}

.register input {
  width: 300px;
  height: 20px;
  font-size: 14px;
  outline-style: none;
  border: 1px solid #ccc;
  border-radius: 3px;
  margin-bottom: 10px;
  padding: 5px;
}
</style>
