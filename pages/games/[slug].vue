<template>
  <div class="min-h-screen container py-10">

    <div class="flex flex-col md:flex-row justify-between gap-6 py-4">
      <div class="w-full md:w-2/5">
        <!-- Banner Section -->
        <div class="relative">
          <img
            src="/assets/images/game/coc.png"
            alt="Weekly Diamond Pass Banner" class="w-full h-[250px] sm:h-[350px] object-cover object-top" />
          <div class="absolute inset-0 bg-gradient-to-b from-transparent to-purple-950/80"></div>
        </div>

        <!-- Title Section -->
        <div class="py-4">
          <h1 class="text-2xl font-bold">Mobile Legends: Bang Bang</h1>

          <div class="flex gap-2 mt-2">
            <div class="bg-white text-purple-900 rounded-full px-4 py-1 text-sm flex items-center">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-1" viewBox="0 0 24 24" fill="none"
                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M12 2L2 7l10 5 10-5-10-5z"></path>
                <path d="M2 17l10 5 10-5"></path>
                <path d="M2 12l10 5 10-5"></path>
              </svg>
              <span>Instant Delivery</span>
            </div>
            <div class="bg-white text-purple-900 rounded-full px-4 py-1 text-sm flex items-center">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-1" viewBox="0 0 24 24" fill="none"
                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"></path>
              </svg>
              <span>Official Distributor</span>
            </div>
          </div>

          <p class="mt-4 text-sm">
            Top up Mobile Legends Diamond in seconds! Just enter your ML user ID, select the value of Diamond you wish
            to
            purchase, complete the payment, and the Diamonds will be added immediately to your ML account.
          </p>

          <p class="mt-2 text-sm">
            Pay conveniently using bKash and Robi. There's no registration, or log-in required!
          </p>

          <p class="mt-2 text-sm">
            Download & play Mobile Legends: Bang Bang today!
          </p>
        </div>
      </div>

      <!-- Form Section -->
      <div class="w-full md:w-3/5">
        <!-- Step 1 -->
        <div class="bg-white rounded-lg p-4 mb-4">
          <div class="flex items-center mb-4">
            <div class="bg-indigo-600 text-white rounded-full w-8 h-8 flex items-center justify-center mr-2">
              1
            </div>
            <h2 class="text-purple-900 text-xl font-bold">Enter User ID</h2>
            <div class="ml-auto">
              <button class="text-indigo-600 bg-indigo-100 rounded-full w-6 h-6 flex items-center justify-center">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" viewBox="0 0 24 24" fill="none"
                  stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <circle cx="12" cy="12" r="10"></circle>
                  <line x1="12" y1="16" x2="12" y2="12"></line>
                  <line x1="12" y1="8" x2="12.01" y2="8"></line>
                </svg>
              </button>
            </div>
          </div>

          <div class="flex flex-col sm:flex-row gap-2 mb-1">
            <div class="flex-1">
              <input type="text" placeholder="Enter User ID"
                class="w-full p-3 border border-gray-300 rounded-lg text-gray-700" v-model="userId" />
              <p class="text-red-500 text-xs mt-1" v-if="userIdError">This field is required</p>
            </div>
            <div class="flex-1">
              <div class="relative">
                <input type="text" placeholder="Zone ID"
                  class="w-full p-3 border border-gray-300 rounded-lg text-gray-700" v-model="zoneId" />
                <div class="absolute inset-y-0 right-0 flex items-center pr-3 pointer-events-none text-gray-400">
                  ( )
                </div>
              </div>
              <p class="text-red-500 text-xs mt-1" v-if="zoneIdError">This field is required</p>
            </div>
          </div>

          <p class="text-gray-500 text-xs">
            To find your User ID, click on your avatar in the top left corner of the main game screen. Then go to the
            "Basic Info" tab. Your user ID is shown below your nickname. Please input the complete user ID here, e.g.
            123456789 (1234).
          </p>
        </div>

        <!-- Step 2 -->
        <div class="bg-white rounded-lg p-4">
          <div class="flex items-center mb-4">
            <div class="bg-indigo-600 text-white rounded-full w-8 h-8 flex items-center justify-center mr-2">
              2
            </div>
            <h2 class="text-purple-900 text-xl font-bold">Select Recharge</h2>
          </div>

          <div class="bg-pink-500 text-white rounded-full px-4 py-2 mb-4 inline-flex items-center">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-1" viewBox="0 0 24 24" fill="none"
              stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <circle cx="12" cy="12" r="10"></circle>
              <polyline points="12 6 12 12 16 14"></polyline>
            </svg>
            <span>15,876 items bought in the last hour</span>
          </div>

          <div class="grid grid-cols-2 gap-4">
            <!-- Diamond Package 1 -->
            <div class="bg-indigo-100 rounded-lg p-4 relative cursor-pointer transition-all duration-200"
              :class="{ 'ring-2 ring-pink-500 shadow-lg transform scale-[1.02]': selectedPackage === 1 }"
              @click="selectPackage(1)">
              <div class="absolute top-0 left-0 bg-pink-500 text-white text-xs px-2 py-1 rounded-br-lg">
                POPULAR
              </div>
              <div class="pt-6">
                <h3 class="text-purple-900 text-xl font-bold">33 Diamonds</h3>
                <p class="text-purple-700 text-sm">(30 + 3 Bonus)</p>

                <div class="flex justify-center my-4">
                  <div class="w-8 h-8 bg-blue-300 rounded-full flex items-center justify-center">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-blue-600" viewBox="0 0 24 24"
                      fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                      <polygon
                        points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2">
                      </polygon>
                    </svg>
                  </div>
                </div>

                <div class="text-center">
                  <p class="text-gray-500 text-xs">From</p>
                  <p class="text-purple-900 font-bold">Tk 50</p>
                </div>
              </div>
            </div>

            <!-- Diamond Package 2 -->
            <div class="bg-indigo-100 rounded-lg p-4 relative cursor-pointer transition-all duration-200"
              :class="{ 'ring-2 ring-pink-500 shadow-lg transform scale-[1.02]': selectedPackage === 2 }"
              @click="selectPackage(2)">
              <div class="pt-6">
                <h3 class="text-purple-900 text-xl font-bold">66 Diamonds</h3>
                <p class="text-purple-700 text-sm">(60 + 6 Bonus)</p>

                <div class="flex justify-center my-4">
                  <div class="w-8 h-8 bg-blue-300 rounded-full flex items-center justify-center">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-blue-600" viewBox="0 0 24 24"
                      fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                      <polygon
                        points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2">
                      </polygon>
                    </svg>
                  </div>
                </div>

                <div class="text-center">
                  <p class="text-gray-500 text-xs">From</p>
                  <p class="text-purple-900 font-bold">Tk 100</p>
                </div>
              </div>
            </div>

            <!-- Diamond Package 3 -->
            <div class="bg-indigo-100 rounded-lg p-4 relative cursor-pointer transition-all duration-200"
              :class="{ 'ring-2 ring-pink-500 shadow-lg transform scale-[1.02]': selectedPackage === 3 }"
              @click="selectPackage(3)">
              <div class="pt-6">
                <h3 class="text-purple-900 text-xl font-bold">131 Diamonds</h3>
                <p class="text-purple-700 text-sm">(119 + 12 Bonus)</p>

                <div class="flex justify-center my-4">
                  <div class="w-8 h-8 bg-blue-300 rounded-full flex items-center justify-center">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-blue-600" viewBox="0 0 24 24"
                      fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                      <polygon
                        points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2">
                      </polygon>
                    </svg>
                  </div>
                </div>

                <div class="text-center">
                  <p class="text-gray-500 text-xs">From</p>
                  <p class="text-purple-900 font-bold">Tk 200</p>
                </div>
              </div>
            </div>

            <!-- Diamond Package 4 -->
            <div class="bg-indigo-100 rounded-lg p-4 relative cursor-pointer transition-all duration-200"
              :class="{ 'ring-2 ring-pink-500 shadow-lg transform scale-[1.02]': selectedPackage === 4 }"
              @click="selectPackage(4)">
              <div class="absolute top-0 left-0 bg-pink-500 text-white text-xs px-2 py-1 rounded-br-lg">
                POPULAR
              </div>
              <div class="pt-6">
                <h3 class="text-purple-900 text-xl font-bold">325 Diamonds</h3>
                <p class="text-purple-700 text-sm">(295 + 30 Bonus)</p>

                <div class="flex justify-center my-4">
                  <div class="w-8 h-8 bg-blue-300 rounded-full flex items-center justify-center">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-blue-600" viewBox="0 0 24 24"
                      fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                      <polygon
                        points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2">
                      </polygon>
                    </svg>
                  </div>
                </div>

                <div class="text-center">
                  <p class="text-gray-500 text-xs">From</p>
                  <p class="text-purple-900 font-bold">Tk 500</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script setup>
import { ref } from 'vue'

const userId = ref('')
const zoneId = ref('')
const userIdError = ref(false)
const zoneIdError = ref(false)

const selectedPackage = ref(null)

const selectPackage = (packageId) => {
  selectedPackage.value = packageId
}

const validateForm = () => {
  userIdError.value = !userId.value
  zoneIdError.value = !zoneId.value
  return userId.value && zoneId.value
}

const submitForm = () => {
  if (validateForm()) {
    // Handle form submission
    console.log('Form submitted', { userId: userId.value, zoneId: zoneId.value })
  }
}
</script>
