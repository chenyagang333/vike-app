<template>
    <template v-if="init">
        <slot />
    </template>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue';
const init = ref<boolean>(false)
onMounted(() => init.value = true)
</script>