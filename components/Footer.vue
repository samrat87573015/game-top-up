<template>
  <footer class="bg-themebg text-white">
    <div class="container mx-auto px-4 py-12">
      <!-- Desktop: 3 columns, Mobile: Stack -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <!-- Column 1: Company Info -->
        <div>
          
          <div class="mb-4">
            <img src="/assets/images/logo/logo.png" alt="Company Logo" class="h-10 mb-2" />
          </div>
          <p class="text-gray-400 mb-4">
            We provide exceptional services and solutions to meet all your needs.
            Our team is dedicated to delivering the best experience possible.
          </p>
          <div class="flex space-x-4">
            <a href="#" class="text-gray-400 hover:text-white transition-colors">
              <Twitter class="h-5 w-5" />
              <span class="sr-only">Twitter</span>
            </a>
            <a href="#" class="text-gray-400 hover:text-white transition-colors">
              <Facebook class="h-5 w-5" />
              <span class="sr-only">Facebook</span>
            </a>
            <a href="#" class="text-gray-400 hover:text-white transition-colors">
              <Instagram class="h-5 w-5" />
              <span class="sr-only">Instagram</span>
            </a>
            <a href="#" class="text-gray-400 hover:text-white transition-colors">
              <Linkedin class="h-5 w-5" />
              <span class="sr-only">LinkedIn</span>
            </a>
          </div>
        </div>

        <!-- Column 2: Quick Links -->
        <div>
          <h3 class="text-xl font-bold mb-4">Quick Links</h3>
          <ul class="space-y-2">
            <li>
              <a href="#" class="text-gray-400 hover:text-white transition-colors">Home</a>
            </li>
            <li>
              <a href="#" class="text-gray-400 hover:text-white transition-colors">About Us</a>
            </li>
            <li>
              <a href="#" class="text-gray-400 hover:text-white transition-colors">Services</a>
            </li>
            <li>
              <a href="#" class="text-gray-400 hover:text-white transition-colors">Blog</a>
            </li>
            <li>
              <a href="#" class="text-gray-400 hover:text-white transition-colors">Contact</a>
            </li>
          </ul>
        </div>

        <!-- Column 3: Contact Info -->
        <div>
          <h3 class="text-xl font-bold mb-4">Contact Us</h3>
          <ul class="space-y-4">
            <li class="flex items-start">
              <MapPin class="h-5 w-5 text-gray-400 mr-2 mt-1 flex-shrink-0" />
              <span class="text-gray-400">
                123 Business Street, Suite 100<br />
                New York, NY 10001
              </span>
            </li>
            <li class="flex items-center">
              <Phone class="h-5 w-5 text-gray-400 mr-2 flex-shrink-0" />
              <a href="tel:+1234567890" class="text-gray-400 hover:text-white transition-colors">
                (123) 456-7890
              </a>
            </li>
            <li class="flex items-center">
              <Mail class="h-5 w-5 text-gray-400 mr-2 flex-shrink-0" />
              <a href="mailto:info@company.com" class="text-gray-400 hover:text-white transition-colors">
                info@company.com
              </a>
            </li>

          </ul>
        </div>
      </div>

      <!-- Bottom Copyright -->
      <div class="border-t border-gray-800 mt-12 pt-6 text-center text-gray-400 text-sm">
        <p>&copy; {{ new Date().getFullYear() }} Company Name. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { ref } from 'vue';
import { Twitter, Facebook, Instagram, Linkedin, MapPin, Phone, Mail } from 'lucide-vue-next';


</script>