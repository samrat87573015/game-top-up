<template>
  <NuxtLink to="/games/fds" class="game_card_item glow-effect rounded-lg overflow-hidden bg-themebg shadow-lg">
    <div class="card_image rounded-lg overflow-hidden">
      <NuxtImg src="/assets/images/game/coc.png" width="230" height="230" />
    </div>
    <div class="card_content text-center py-4 px-1 text-white">
      <NuxtLink to="/"><h3 class="card_title text-[13px] sm:text-base font-semibold lg:tracking-wider mb-2 transition duration-300">Clash of Clans</h3></NuxtLink>
      <p class="text-[11px] sm:text-sm text-gray-200">Sep 14, 2025</p>
    </div>
  </NuxtLink>
</template>

<style>
/* Custom glow effect using Tailwind-like approach */
.glow-effect {
  box-shadow: 0 0 15px rgba(81, 39, 163, 0.7); /* Purple glow similar to the image */
  transition: box-shadow 0.3s ease-in-out;
}

.glow-effect:hover {
  box-shadow: 0 0 25px rgba(147, 112, 219, 0.9); /* Stronger glow on hover */
}


</style>