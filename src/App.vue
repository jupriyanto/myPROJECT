<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>
<template>
  <header>

      <div class="container w-full mx-auto">
          <div class="border-b border-gray-200 dark:border-gray-700 ">
              <nav>
                  <ul
                      class="flex flex-wrap -mb-px text-sm font-medium justify-center text-center text-gray-500 dark:text-gray-400">
                      <li class="mr-2">
                          <RouterLink to="/" 
                              class="inline-flex p-4 border-transparent rounded-t-lg hover:text-gray-600 hover:border-gray-300 dark:hover:text-gray-300 group">
                              Beranda
                          </RouterLink>
                      </li>
                      <li class="mr-2">
                          <RouterLink to="/myapp" 
                              class="inline-flex p-4 border-transparent rounded-t-lg hover:text-gray-600 hover:border-gray-300 dark:hover:text-gray-300 group">
                              MyApp
                          </RouterLink>
                      </li>
                      <li class="mr-2">
                          <RouterLink to="/about" 
                              class="inline-flex p-4 border-transparent rounded-t-lg hover:text-gray-600 hover:border-gray-300 dark:hover:text-gray-300 group">
                              About
                          </RouterLink>
                      </li>
                  </ul>
              </nav>
          </div>

      </div>
  </header>

  <RouterView />
</template>