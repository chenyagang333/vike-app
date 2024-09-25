<template>
  <h1>Welcome</h1>
  This page is:
  <InitApp>
    <img v-show="loadSuccess" style="width: 200px;" @load="handleImageLoad"
      src="https://learn.microsoft.com/zh-cn/dotnet/architecture/microservices/multi-container-microservice-net-applications/media/microservice-application-design/multi-architectural-patterns-polyglot-microservices.png" />
    <template v-if="!loadSuccess">
      <div class="loader"></div>
    </template>
  </InitApp>
  <ul>
    <li>Rendered to HTML.</li>
    <li>Interactive.
      <Counter />
    </li>
  </ul>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import Counter from "./Counter.vue";
import InitApp from '../../components/InitApp.vue';

const loadSuccess = ref<boolean>(false)

const handleImageLoad = (event: any) => {
  loadSuccess.value = true
  console.log('Image loaded successfully', event.target);
}
</script>

<style>
.loader {
  border: 16px solid #f3f3f3;
  /* Light grey */
  border-top: 16px solid #3498db;
  /* Blue */
  border-radius: 50%;
  width: 120px;
  height: 120px;
  animation: spin 2s linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}
</style>
