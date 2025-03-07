<template>
  <NuxtLink to="/games/fds" class="game_card_item glow-effect rounded-lg overflow-hidden theme-bg shadow-lg">
    <div class="card_image w-full h-[150px] xl:h-[190px] rounded-lg overflow-hidden">
      <img src="/assets/images/game/coc.png" alt="game_imaeg" class="w-full h-full object-cover" />
    </div>
    <div class="card_content text-center py-4 text-white">
      <NuxtLink to="/"><h3 class="card_title text-base font-semibold tracking-wider mb-2 transition duration-300">Clash of Clans</h3></NuxtLink>
      <p class="text-sm text-gray-200">Sep 14, 2025</p>
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