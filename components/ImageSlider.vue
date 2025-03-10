<template>
  <div class="w-full mt-0">
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
          <div class="relative  bg-gray-100 overflow-hidden">
            <NuxtImg :src="slide.image" width="1504" height="250" />
          </div>
        </swiper-slide>
      </swiper>
      
      <!-- Custom navigation buttons -->
      <!-- <div class="hidden md:block">
        <button class="swiper-button-prev-custom absolute top-1/2 left-4 -translate-y-1/2 dark-theme  text-white p-3 rounded-full shadow-md z-10 transition-all cursor-pointer">
          <LucideChevronLeft class="w-5 h-5" />
        </button>
        <button class="swiper-button-next-custom absolute top-1/2 right-4 -translate-y-1/2 dark-theme  text-white p-3 rounded-full shadow-md z-10 transition-all cursor-pointer">
          <LucideChevronRight class="w-5 h-5" />
        </button>
      </div> -->
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
    image: 'https://jubaly.com/wp-content/uploads/2024/05/%E0%A6%A8%E0%A6%BF%E0%A6%9C%E0%A7%87%E0%A6%B0-%E0%A6%AC%E0%A7%87%E0%A6%A1-%E0%A6%B0%E0%A7%81%E0%A6%AE%E0%A6%95%E0%A7%87-%E0%A6%97%E0%A7%87%E0%A6%AE%E0%A6%BF%E0%A6%82-%E0%A6%B0%E0%A7%81%E0%A6%AE%E0%A7%87-%E0%A6%B0%E0%A7%82%E0%A6%AA%E0%A6%BE%E0%A6%A8%E0%A7%8D%E0%A6%A4%E0%A6%B0%E0%A6%BF%E0%A6%A4-%E0%A6%95%E0%A6%B0%E0%A6%A4%E0%A7%87.webp'
  },
  {
    title: 'Coastal Getaway',
    description: 'Relax by the ocean with stunning coastal views',
    image: 'https://jubaly.com/wp-content/uploads/2023/03/jubaly-banner-ew.webp'
  },
  
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