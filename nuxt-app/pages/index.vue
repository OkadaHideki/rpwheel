<template>
    <v-container>
      <h1>テスト</h1>
      <v-card v-if="data" class="ma-3">
        <v-card-title>from json server...</v-card-title>
        <v-card-subtitle>
          <!-- JSONデータをフォーマットして表示 -->
          <pre>{{ data }}</pre>
        </v-card-subtitle>
      </v-card>
      <v-alert v-else type="info">データを読み込み中...</v-alert>
    </v-container>
  </template>
  
  <script setup>
  import { ref, onMounted, onUnmounted } from 'vue';
  import axios from 'axios';
  
  const data = ref(null);
  const fetchInterval = 5000; // 5秒ごとにデータを更新
  let intervalId = null;
  
  const fetchData = async () => {
    try {
      const response = await axios.get('http://153.127.216.75:3003/api');
      data.value = response.data;
    } catch (error) {
      console.error('データの取得に失敗しました:', error);
    }
  };
  
  const startFetching = () => {
    fetchData(); // 初回のデータ取得
    intervalId = setInterval(fetchData, fetchInterval); // 定期的にデータを取得
  };
  
  const stopFetching = () => {
    if (intervalId) {
      clearInterval(intervalId); // 定期的なデータ取得を停止
    }
  };
  
  onMounted(() => {
    startFetching();
  });
  
  onUnmounted(() => {
    stopFetching();
  });
  </script>
  
  <style scoped>
  /* 必要に応じてスタイルを追加 */
  </style>
  