<script setup>
import { computed } from 'vue'
import { useMainStore } from '@/stores/main'
import menu from '@/menu.js'
import NavBar from '@/components/NavBar.vue'
import AsideMenu from '@/components/AsideMenu.vue'
import FooterBar from '@/components/FooterBar.vue'
import Overlay from '@/components/Overlay.vue'

const mainStore = useMainStore()

mainStore.fullScreenToggle(false)

mainStore.setUser({
  name: 'John Doe',
  email: 'john@example.com',
  avatar: 'https://avatars.dicebear.com/api/avataaars/example.svg?options[top][]=shortHair&options[accessoriesChance]=93'
})

const isAsideLgActive = computed(() => mainStore.isAsideLgActive)

const overlayClick = () => {
  mainStore.asideLgToggle(false)
}
</script>

<template>
  <nav-bar />
  <aside-menu :menu="menu" />
  <slot />
  <footer-bar />
  <overlay
    v-show="isAsideLgActive"
    z-index="z-30"
    @overlay-click="overlayClick"
  />
</template>
