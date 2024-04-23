<script setup lang="ts">
import { installPrompt } from './utils/pwa'
import { appName } from '~/constants'

// https://nuxt.com/docs/api/composables/use-head
useHead({
  title: appName,
  meta: [
    {
      name: 'description',
      content: '好的，今天我们来做菜！',
    },
  ],
})

const indexedDB = useIndexedDB()
console.log("Initted the db ----------------")
onMounted(() => {
  installPrompt()
  indexedDB.init()
})
</script>

<template>
  <VitePwaManifest />
  <NuxtLayout>
    <NuxtLoadingIndicator />
    <NuxtPage />
  </NuxtLayout>
</template>
