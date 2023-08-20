<script setup lang="ts">
import { ref } from 'vue';
import ArticleContent from '../components/ArticleContent.vue';


interface articleData {
  title: string;
  content: string;
  // completed: boolean;
  // date: string;
  // time: string;
}

const newarticleData = ref<articleData>({
  title: '',
  content: '',
  // completed: false,
  // date: '',
  // time: ''
});
const articleDatas = ref<articleData[]>([]);

const addArticle = () => {
  if (newarticleData.value.title.trim() !== '') {
    articleDatas.value.push({ ...newarticleData.value });
    newarticleData.value = { title: '', content: '' };
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
    <div class="articleContent">
      <h2>新增貼文</h2>
      <a href="login.html">
        <button class="loginbtn">登入</button></a>
      <div class="newpost">
        <input v-model="newarticleData.title" type="text" placeholder="輸入文章標題" />
        <textarea v-model="newarticleData.content" type="text" placeholder="輸入文章內容" cols="30" rows="10">
        </textarea>
      </div>
      <button @click="addArticle">發布貼文</button>

    </div>
    <div class="articleData-list">
      <div class="articleData-item" v-for="(articleData, index) in articleDatas" :key="index">
        <ArticleContent :articleData="articleData" @delete="deleteArticle(index)" />
      </div>

    </div>

  </div>
</template>

<style scoped>
/* 發文頁面 */
.articleContent {
  margin-bottom: 10px;
  position: relative;
}

.loginbtn {
  position: absolute;
  top: 0;
  right: 0;
  color: white;
  background-color: #213547;
}

.newpost {
  margin-bottom: 10px;
}

.newpost input {
  width: 100%;
  height: 30px;
  margin-bottom: 10px;
  border: 1.5px solid #213547;
  border-radius: 5px;
  font-size: 16px;
  padding: 5px;
}

.newpost textarea {
  width: 100%;
  padding: 5px;
}

.newpost input:nth-child(2) {
  height: 150px;
  vertical-align: text-top;
}

.articleData-list {
  /* border: 2px solid #213547; */
  padding: 5px;
}</style>
