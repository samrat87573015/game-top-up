<template>
  <header class="header_area">
    <!-- Top section with logo and menu -->
    <div class="container mx-auto px-4 py-4">
      <div class="flex justify-between items-center">
        <!-- Logo -->
        <div class="flex items-center">
          <NuxtLink to="/" class="text-2xl font-bold text-gray-800">
            <img src="/assets/images/logo/logo.png" alt="Logo" class="h-10" />
          </NuxtLink>
        </div>

        <!-- Menu Items -->
        <nav class="hidden md:flex space-x-8">
          <NuxtLink to="/" class="nav-link">Home</NuxtLink>
          <NuxtLink to="/" class="nav-link">Products</NuxtLink>
          <NuxtLink to="/" class="nav-link">Services</NuxtLink>
          <NuxtLink to="/about" class="nav-link">About</NuxtLink>
          <NuxtLink to="/" class="nav-link">Contact</NuxtLink>
        </nav>

        <!-- Mobile Menu Button -->
        <div class="md:hidden">
          <button @click="toggleMenu" class="text-gray-700 focus:outline-none">
            <LucideAlignJustify />
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Menu Overlay (Fade effect) -->
    <transition name="fade">
      <div
        v-if="isMenuOpen"
        class="fixed inset-0 bg-black opacity-[0.5] z-50"
        @click="toggleMenu"
      ></div>
    </transition>

    <!-- Mobile Menu (Slide-in effect) -->
    <transition name="slide">
      <div
        v-if="isMenuOpen"
        class="fixed top-0 left-0 w-64 h-full bg-[#02102B] shadow-lg p-6 z-50"
        @click.stop
      >
        <button
          @click="toggleMenu"
          class="absolute top-4 right-4 text-gray-600"
        >
          <LucideX />
        </button>
        <div class="flex flex-col space-y-3 mt-8">
          <NuxtLink to="/" class="nav-link" @click="toggleMenu">Home</NuxtLink>
          <NuxtLink to="/" class="nav-link" @click="toggleMenu">Products</NuxtLink>
          <NuxtLink to="/" class="nav-link" @click="toggleMenu">Services</NuxtLink>
          <NuxtLink to="/about" class="nav-link" @click="toggleMenu">About</NuxtLink>
          <NuxtLink to="/" class="nav-link" @click="toggleMenu">Contact</NuxtLink>
        </div>
      </div>
    </transition>

    <!-- Search Bar -->
    <div class="border-t border-gray-200">
      <div class="container mx-auto px-4 py-3">
        <div class="relative">
          <input
            type="text"
            placeholder="Search for products, services, and more..."
            class="w-full pl-10 pr-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-gray-200"
            v-model="searchQuery"
            @keyup.enter="handleSearch"
          />
          <div class="absolute left-3 top-1/2 transform -translate-y-1/2 text-gray-400">
            <LucideSearch />
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from "vue";

const isMenuOpen = ref(false);
const searchQuery = ref("");

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>

<style>
/* Slide-in transition for menu */
.slide-enter-active,
.slide-leave-active {
  transition: transform 0.3s ease-in-out;
}

.slide-enter-from,
.slide-leave-to {
  transform: translateX(-100%);
}

/* Fade transition for overlay */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease-in-out;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
