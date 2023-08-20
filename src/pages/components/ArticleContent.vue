<template>
  <div class="articleData-line">
    <div class="articleData">

      <img src="" alt="">
      <p>Name</p>
      <TimeDisplay />
      <input v-if="articleData" v-model="articleData.title" readonly />
      <textarea v-if="articleData" v-model="articleData.content" readonly ></textarea>
    </div>
    <a href="#">觀看詳細文章內容</a>
    <button @click="deleteArticle">刪除</button>
    
  </div>
</template>
  
<script setup lang="ts">
import TimeDisplay from './TimeDisplay.vue';

interface articleData {
  title: string;
  content: string;
  // completed: boolean;
  // date: string;
  // time: string;
}

const props = defineProps({
  articleData: Object as () => articleData
});

const emit = defineEmits();

const deleteArticle = () => {
  emit('delete', props.articleData);
};

</script>
  
<style>
.articleData-line {
  width: 100%;
  border-bottom: 1px solid #213547;
  margin-bottom: 10px;
  padding-bottom: 10px;
  /* display: flex; */
  justify-content: space-between;
  text-align: left;
}

.articleData input {
  display: block;
  width: 100%;
  height: 30px;
  margin-top: 10px;
  margin-bottom: 10px;
  border: unset;
  outline:none;
  font-size: 16px;
}

.articleData input:nth-child(2){
  font-size: 20px;
  font-weight: bold;
}

.articleData textarea{
  width: 100%;
  border: unset;
  resize:none;
  outline:none;
}
</style>