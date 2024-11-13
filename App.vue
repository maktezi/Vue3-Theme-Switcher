<template>
  <div>
    <button @click="toggleTheme">Toggle Theme</button>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

const root = document.documentElement
const darkThemeHex = '#333'
const lightThemeHex = '#42b983'
const isDarkTheme = ref(false)

watch(isDarkTheme, (oldValue, newValue) => {
  const newColor = newValue ? lightThemeHex : darkThemeHex
  root.style.setProperty('--main-color', newColor)
})

const toggleTheme = () => isDarkTheme.value = !isDarkTheme.value
</script>

<style>
:root {
  --main-color: #42b983;
}

body {
  background-color: var(--main-color);
}
</style>
