<template>
  <nav class="navbar-container">
    <!-- Top Bar -->
    <div class="navbar-header">
      <div class="navbar-left">
        <img src="@/assets/logo.svg" alt="Logo" class="logo" />
        <span class="brand">ENET</span>
      </div>

      <div class="navbar-right">
        <img src="@/assets/logo.svg" alt="Right Logo" class="right-logo" />
      </div>
    </div>

    <!-- Bottom Navigation Bar -->
    <div class="navbar-menu" :class="{ open: mobileMenuOpen }">
      <div class="nav-links-wrapper">
        <div class="nav-item">
          <a href="#about" class="nav-link">About</a>
        </div>
        <div class="nav-item dropdown">
          <button @click="toggleDropdown('services')" class="nav-link dropdown-toggle">
            Services
            <span class="dropdown-icon" :class="{ active: dropdownOpen.services }">▼</span>
          </button>
          <div class="dropdown-menu" v-if="dropdownOpen.services">
            <a href="#service1" @click="closeDropdown">Service 1</a>
            <a href="#service2" @click="closeDropdown">Service 2</a>
            <a href="#service3" @click="closeDropdown">Service 3</a>
          </div>
        </div>
        <div class="nav-item">
          <a href="#contact" class="nav-link">Contact</a>
        </div>
      </div>

      <button
        class="burger"
        :aria-expanded="mobileMenuOpen.toString()"
        :class="{ open: mobileMenuOpen }"
        type="button"
        @click="toggleMobileMenu"
        aria-label="Toggle navigation"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>
    </div>
  </nav>
</template>

<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue'

const mobileMenuOpen = ref(false)
const dropdownOpen = ref({
  services: false
})

const isHidden = ref(false)

let lastScroll = 0

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const toggleDropdown = (dropdown: string) => {
  dropdownOpen.value[dropdown] = !dropdownOpen.value[dropdown]
}

const closeDropdown = () => {
  dropdownOpen.value.services = false
}

const handleScroll = () => {
  const current = window.pageYOffset || document.documentElement.scrollTop
  // if scrolling down and past 60px, hide header; if scrolling up show it
  if (current > lastScroll && current > 60) {
    isHidden.value = true
  } else {
    isHidden.value = false
  }
  lastScroll = current <= 0 ? 0 : current
}

onMounted(() => {
  lastScroll = window.pageYOffset || document.documentElement.scrollTop
  window.addEventListener('scroll', handleScroll, { passive: true })
})

onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style src="./Navbar.css" scoped></style>
