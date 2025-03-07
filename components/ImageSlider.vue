<template>
  <div class="w-full">
    <div class="relative container">
      <!-- Swiper container -->
      <swiper
        :modules="[SwiperNavigation, SwiperPagination, SwiperAutoplay]"
        :slides-per-view="1"
        :space-between="30"
        :loop="true"
        :pagination="{ clickable: true }"
        :navigation="true"
        :autoplay="{ delay: 3000, disableOnInteraction: false }"
        class="mySwiper overflow-hidden"
        
      >
        <swiper-slide v-for="(slide, index) in slides" :key="index">
          <div class="relative h-64 md:h-80 bg-gray-100 overflow-hidden">
            <img 
              :src="slide.image" 
              :alt="slide.title"
              class="w-full h-full object-cover transition-transform duration-500"
            />
          </div>
        </swiper-slide>
      </swiper>
      
      <!-- Custom navigation buttons -->
      <div class="hidden md:block">
        <button class="swiper-button-prev-custom absolute top-1/2 left-4 -translate-y-1/2 dark-theme  text-white p-3 rounded-full shadow-md z-10 transition-all cursor-pointer">
          <LucideChevronLeft class="w-5 h-5" />
        </button>
        <button class="swiper-button-next-custom absolute top-1/2 right-4 -translate-y-1/2 dark-theme  text-white p-3 rounded-full shadow-md z-10 transition-all cursor-pointer">
          <LucideChevronRight class="w-5 h-5" />
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Navigation, Pagination, Autoplay } from 'swiper/modules';


// Import Swiper styles
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';

// Define modules
const SwiperNavigation = Navigation;
const SwiperPagination = Pagination;
const SwiperAutoplay = Autoplay;

// Sample slide data
const slides = ref([
  {
    title: 'Mountain Retreat',
    description: 'Explore the serene beauty of mountain landscapes',
    image: 'https://images.unsplash.com/photo-1506905925346-21bda4d32df4?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80'
  },
  {
    title: 'Coastal Getaway',
    description: 'Relax by the ocean with stunning coastal views',
    image: 'https://images.unsplash.com/photo-1507525428034-b723cf961d3e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80'
  },
  {
    title: 'Urban Adventure',
    description: 'Discover the excitement of city exploration',
    image: 'https://images.unsplash.com/photo-1480714378408-67cf0d13bc1b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80'
  },
  {
    title: 'Forest Escape',
    description: 'Find peace among ancient trees and lush greenery',
    image: 'https://images.unsplash.com/photo-1448375240586-882707db888b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80'
  },
  {
    title: 'Desert Solitude',
    description: 'Experience the stark beauty of desert landscapes',
    image: 'https://images.unsplash.com/photo-1509316785289-025f5b846b35?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80'
  }
]);

onMounted(() => {
  // Custom navigation setup
  const prevBtn = document.querySelector('.swiper-button-prev-custom');
  const nextBtn = document.querySelector('.swiper-button-next-custom');
  
  if (prevBtn && nextBtn) {
    prevBtn.addEventListener('click', () => {
      document.querySelector('.swiper-button-prev').click();
    });
    
    nextBtn.addEventListener('click', () => {
      document.querySelector('.swiper-button-next').click();
    });
  }
});
</script>

<style>
/* Hide default Swiper navigation arrows but keep functionality */
:root {
  --swiper-theme-color: #3b82f6;
  --swiper-navigation-size: 0;
}

.swiper-button-prev, .swiper-button-next {
  opacity: 0;
}

/* Custom pagination styling */
.swiper-pagination-bullet {
  width: 10px;
  height: 10px;
  background-color: white;
  opacity: 0.5;
}

.swiper-pagination-bullet-active {
  opacity: 1;
  background-color: white;
}
</style>