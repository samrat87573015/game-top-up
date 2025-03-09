<template>
  <div class="min-h-screen container py-10">
    <div class="flex flex-col md:flex-row justify-between gap-6 py-4">
      <!-- Left Area (Static) -->
      <div class="w-full md:w-2/5">
        <!-- Banner Section -->
        <div class="relative">
          <img src="/assets/images/game/coc.png" alt="Weekly Diamond Pass Banner"
            class="w-full h-[250px] sm:h-[350px] object-cover object-top" />
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
            to purchase, complete the payment, and the Diamonds will be added immediately to your ML account.
          </p>

          <p class="mt-2 text-sm">
            Pay conveniently using bKash and Robi. There's no registration, or log-in required!
          </p>

          <p class="mt-2 text-sm">
            Download & play Mobile Legends: Bang Bang today!
          </p>
        </div>


      </div>

      <!-- Right Area (Sliding) -->
      <div class="w-full md:w-3/5">
        <!-- Progress Bar -->
        <div class="mb-6 px-4">
          <div class="w-full bg-gray-200 rounded-full h-2.5">
            <div class="bg-theme h-2.5 rounded-full transition-all duration-500"
              :style="{ width: `${(currentStep / totalSteps) * 100}%` }"></div>
          </div>
          <div class="flex justify-between mt-2 text-sm text-gray-500">
            <span>User Info & Package</span>
            <span>Payment</span>
          </div>
        </div>

        <div class="overflow-hidden">
          <div class="flex transition-transform duration-500 ease-in-out"
            :style="{ transform: `translateX(-${(currentStep - 1) * 100}%)` }">

            <!-- Step 1: User Info & Package Selection -->
            <div class="w-full px-4 flex-shrink-0">
              <!-- User Info Section -->
              <div class="bg-white rounded-lg p-4 mb-4">
                <div class="flex items-center mb-4">
                  <div class="bg-theme2 text-white rounded-full w-8 h-8 flex items-center justify-center mr-2">
                    1
                  </div>
                  <h2 class="text-theme text-xl font-bold">Enter User ID</h2>
                  <div class="ml-auto">
                    <button class="text-theme bg-indigo-100 rounded-full w-6 h-6 flex items-center justify-center">
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
                  To find your User ID, click on your avatar in the top left corner of the main game screen. Then go to
                  the
                  "Basic Info" tab. Your user ID is shown below your nickname. Please input the complete user ID here,
                  e.g.
                  123456789 (1234).
                </p>
              </div>

              <!-- Package Selection Section -->
              <div class="bg-white rounded-lg p-4">
                <div class="flex items-center mb-4">
                  <div class="bg-theme2 text-white rounded-full w-8 h-8 flex items-center justify-center mr-2">
                    2
                  </div>
                  <h2 class="text-theme text-xl font-bold">Select Recharge</h2>
                </div>

                <div class="bg-theme text-white rounded-full px-4 py-2 mb-4 inline-flex items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-1" viewBox="0 0 24 24" fill="none"
                    stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <circle cx="12" cy="12" r="10"></circle>
                    <polyline points="12 6 12 12 16 14"></polyline>
                  </svg>
                  <span>15,876 items bought in the last hour</span>
                </div>

                <div class="grid grid-cols-2 lg:grid-cols-4 gap-4">
                  <!-- Diamond Package 1 -->
                  <div
                    class="bg-indigo-100 overflow-hidden rounded-lg p-4 relative cursor-pointer transition-all duration-200"
                    :class="{ 'ring-2 ring-theme shadow-lg transform scale-[1.02]': selectedPackage === 1 }"
                    @click="selectPackage(1)">
                    <div class="absolute top-0 left-0 bg-theme text-white text-xs px-2 py-1 rounded-br-lg">
                      POPULAR
                    </div>
                    <div class="pt-6">
                      <h3 class="text-theme text-xl font-bold">33 Diamonds</h3>
                      <p class="text-theme text-sm">(30 + 3 Bonus)</p>

                      <div class="flex justify-center my-4">
                        <div class="w-20 h-20 flex items-center justify-center">
                          <img src="/assets/images/icon/ucImg.png" alt="">
                        </div>
                      </div>

                      <div class="text-center">
                        <p class="text-gray-500 text-xs">From</p>
                        <p class="text-theme font-bold">Tk 50</p>
                      </div>
                    </div>
                  </div>
                  <!-- Diamond Package 2 -->
                  <div
                    class="bg-indigo-100 overflow-hidden rounded-lg p-4 relative cursor-pointer transition-all duration-200"
                    :class="{ 'ring-2 ring-theme shadow-lg transform scale-[1.02]': selectedPackage === 2 }"
                    @click="selectPackage(2)">

                    <div class="pt-6">
                      <h3 class="text-theme text-xl font-bold">66 Diamonds</h3>
                      <p class="text-theme text-sm">(60 + 6 Bonus)</p>

                      <div class="flex justify-center my-4">
                        <div class="w-20 h-20 flex items-center justify-center">
                          <img src="/assets/images/icon/ucImg.png" alt="">
                        </div>
                      </div>

                      <div class="text-center">
                        <p class="text-gray-500 text-xs">From</p>
                        <p class="text-theme font-bold">Tk 100</p>
                      </div>
                    </div>
                  </div>
                  <!-- Diamond Package 3 -->
                  <div
                    class="bg-indigo-100 overflow-hidden rounded-lg p-4 relative cursor-pointer transition-all duration-200"
                    :class="{ 'ring-2 ring-theme shadow-lg transform scale-[1.02]': selectedPackage === 3 }"
                    @click="selectPackage(3)">
                    <div class="absolute top-0 left-0 bg-theme text-white text-xs px-2 py-1 rounded-br-lg">
                      POPULAR
                    </div>
                    <div class="pt-6">
                      <h3 class="text-theme text-xl font-bold">110 Diamonds</h3>
                      <p class="text-theme text-sm">(100 + 10 Bonus)</p>

                      <div class="flex justify-center my-4">
                        <div class="w-20 h-20 flex items-center justify-center">
                          <img src="/assets/images/icon/ucImg.png" alt="">
                        </div>
                      </div>

                      <div class="text-center">
                        <p class="text-gray-500 text-xs">From</p>
                        <p class="text-theme font-bold">Tk 150</p>
                      </div>
                    </div>
                  </div>
                  <!-- Diamond Package 4 -->
                  <div
                    class="bg-indigo-100 overflow-hidden rounded-lg p-4 relative cursor-pointer transition-all duration-200"
                    :class="{ 'ring-2 ring-theme shadow-lg transform scale-[1.02]': selectedPackage === 4 }"
                    @click="selectPackage(4)">

                    <div class="pt-6">
                      <h3 class="text-theme text-xl font-bold">220 Diamonds</h3>
                      <p class="text-theme text-sm">(200 + 20 Bonus)</p>

                      <div class="flex justify-center my-4">
                        <div class="w-20 h-20 flex items-center justify-center">
                          <img src="/assets/images/icon/ucImg.png" alt="">
                        </div>
                      </div>

                      <div class="text-center">
                        <p class="text-gray-500 text-xs">From</p>
                        <p class="text-theme font-bold">Tk 250</p>
                      </div>
                    </div>
                  </div>
                </div>
              </div>

              <div class="flex justify-end mt-4">
                <button @click="nextStep" :disabled="!canProceedToPayment" :class="[
                  'px-6 py-2 rounded-lg transition-colors duration-300',
                  canProceedToPayment ? 'bg-theme text-white hover:bg-theme2' : 'bg-gray-300 text-gray-500 cursor-not-allowed'
                ]">
                  Next
                </button>
              </div>
            </div>

            <!-- Step 2: Payment Form -->
            <div class="w-full px-4 flex-shrink-0">

              <!-- Order Summary (Shows in step 2) -->
              <div v-if="currentStep === 2" class="bg-white text-gray-600 rounded-lg p-4 my-4">
                <h2 class="text-theme text-xl font-bold mb-2">Order Summary</h2>
                <div class="flex justify-between items-center mb-2">
                  <span class="text-gray-600">User ID:</span>
                  <span class="font-medium">{{ userId }}</span>
                </div>
                <div class="flex justify-between items-center mb-2">
                  <span class="text-gray-600">Zone ID:</span>
                  <span class="font-medium">{{ zoneId }}</span>
                </div>
                <div v-if="selectedPackage" class="flex justify-between items-center mb-2">
                  <span class="text-gray-600">Selected Package:</span>
                  <span class="font-medium">{{ getPackageDetails(selectedPackage).name }}</span>
                </div>
                <div v-if="selectedPackage" class="flex justify-between items-center mb-2">
                  <span class="text-gray-600">Price:</span>
                  <span class="font-bold text-theme">Tk {{ getPackageDetails(selectedPackage).price }}</span>
                </div>
                <div class="flex justify-between items-center mt-2">
                  <span class="text-gray-600">Service Fee:</span>
                  <span>Tk {{ serviceFee }}</span>
                </div>
                <div class="flex justify-between font-bold text-lg border-t border-gray-200 pt-2 mt-2">
                  <span>Total:</span>
                  <span class="text-theme">Tk {{ calculateTotal() }}</span>
                </div>
              </div>


              <div class="bg-white rounded-lg p-4">
                <div class="flex items-center mb-4">
                  <div class="bg-theme2 text-white rounded-full w-8 h-8 flex items-center justify-center mr-2">
                    3
                  </div>
                  <h2 class="text-theme text-xl font-bold">Payment Information</h2>
                </div>

                <!-- Payment Methods -->
                <div class="mb-4">
                  <h3 class="font-medium mb-2">Select Payment Method</h3>
                  <div class="grid grid-cols-3 gap-2">
                    <div v-for="method in paymentMethods" :key="method.id" @click="selectPaymentMethod(method.id)"
                      :class="[
                        'border rounded-lg p-3 flex flex-col items-center cursor-pointer transition-all duration-200',
                        paymentMethod === method.id ? 'border-theme bg-indigo-50' : 'border-gray-200'
                      ]">
                      <img :src="method.icon" :alt="method.name" class="h-8 mb-2">
                      <span class="text-sm">{{ method.name }}</span>
                    </div>
                  </div>
                </div>

                <!-- Contact Information -->
                <div class="mb-4">
                  <h3 class="font-medium mb-2">Contact Information</h3>
                  <div class="mb-3">
                    <label class="block text-sm text-gray-600 mb-1">Phone Number</label>
                    <input type="tel" v-model="phoneNumber" placeholder="Enter your phone number"
                      class="w-full p-3 border border-gray-300 rounded-lg text-gray-700" />
                    <p class="text-red-500 text-xs mt-1" v-if="phoneNumberError">Valid phone number is required</p>
                  </div>
                  <div class="mb-3">
                    <label class="block text-sm text-gray-600 mb-1">Email</label>
                    <input type="email" v-model="email" placeholder="Enter your email address"
                      class="w-full p-3 border border-gray-300 rounded-lg text-gray-700" />
                  </div>
                </div>

                <!-- Terms and Conditions -->
                <div class="mb-4">
                  <label class="flex items-start">
                    <input type="checkbox" v-model="agreeToTerms" class="mt-1 mr-2">
                    <span class="text-sm text-gray-600">
                      I agree to the <a href="#" class="text-theme">Terms of Service</a> and <a href="#"
                        class="text-theme">Privacy Policy</a>
                    </span>
                  </label>
                  <p class="text-red-500 text-xs mt-1" v-if="termsError">You must agree to the terms</p>
                </div>
              </div>

              <div class="flex justify-between mt-4">
                <button @click="prevStep"
                  class="bg-gray-200 text-gray-700 px-6 py-2 rounded-lg hover:bg-gray-300 transition-colors duration-300">
                  Back
                </button>
                <button @click="submitOrder"
                  class="bg-theme text-white px-6 py-2 rounded-lg hover:bg-theme2 transition-colors duration-300">
                  Complete Order
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

// Form state
const currentStep = ref(1)
const totalSteps = 2

const userId = ref('')
const zoneId = ref('')
const userIdError = ref(false)
const zoneIdError = ref(false)

const selectedPackage = ref(null)
const serviceFee = 5

const paymentMethod = ref(null)
const phoneNumber = ref('')
const email = ref('')
const agreeToTerms = ref(false)
const phoneNumberError = ref(false)
const termsError = ref(false)

// Package data
const packages = [
  { id: 1, name: '33 Diamonds (30 + 3 Bonus)', price: 50 },
  { id: 2, name: '66 Diamonds (60 + 6 Bonus)', price: 100 },
  { id: 3, name: '110 Diamonds (100 + 10 Bonus)', price: 150 },
  { id: 4, name: '220 Diamonds (200 + 20 Bonus)', price: 250 }
]

// Payment methods
const paymentMethods = [
  { id: 'bkash', name: 'bKash', icon: '/assets/images/payment/bkash.png' },
  { id: 'nagad', name: 'Nagad', icon: '/assets/images/payment/nagad.png' },
  { id: 'card', name: 'Card', icon: '/assets/images/payment/card.png' }
]

// Computed properties
const canProceedToPayment = computed(() => {
  return userId.value && zoneId.value && selectedPackage.value
})

// Helper functions
const getPackageDetails = (packageId) => {
  return packages.find(pkg => pkg.id === packageId) || { name: '', price: 0 }
}

const calculateTotal = () => {
  if (!selectedPackage.value) return serviceFee
  return getPackageDetails(selectedPackage.value).price + serviceFee
}

const selectPackage = (packageId) => {
  selectedPackage.value = packageId
}

const selectPaymentMethod = (methodId) => {
  paymentMethod.value = methodId
}

// Navigation functions
const validateStep1 = () => {
  userIdError.value = !userId.value
  zoneIdError.value = !zoneId.value
  return userId.value && zoneId.value && selectedPackage.value
}

const validateStep2 = () => {
  phoneNumberError.value = !phoneNumber.value || phoneNumber.value.length < 10
  termsError.value = !agreeToTerms.value
  return phoneNumber.value && phoneNumber.value.length >= 10 && agreeToTerms.value
}

const nextStep = () => {
  if (currentStep.value === 1) {
    if (!validateStep1()) return
  }

  if (currentStep.value < totalSteps) {
    currentStep.value++
  }
}

const prevStep = () => {
  if (currentStep.value > 1) {
    currentStep.value--
  }
}

const submitOrder = () => {
  if (!validateStep2()) return

  // Here you would typically submit the order to your backend
  alert('Order submitted successfully!')

  // For demo purposes, we'll just log the order details
  console.log('Order submitted', {
    userId: userId.value,
    zoneId: zoneId.value,
    package: getPackageDetails(selectedPackage.value),
    paymentMethod: paymentMethod.value,
    phoneNumber: phoneNumber.value,
    email: email.value,
    total: calculateTotal()
  })
}
</script>
