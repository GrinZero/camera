<script setup lang="ts">
import { useConfigStore } from '@renderer/stores/useConfigStore'
import Camera from './components/Camera.vue'
import Setting from './components/Setting.vue'
import Updater from './components/Updater.vue'

const { config } = useConfigStore()

//右键菜单
const contextMenu = () => window.api.contextMenu()
</script>

<template>
  <Suspense>
    <main class="relative" @contextmenu="contextMenu">
      <Updater />
      <section>
        <Camera v-if="config.page == 'camera'" />
        <Setting v-else />
      </section>
    </main>
  </Suspense>
</template>
