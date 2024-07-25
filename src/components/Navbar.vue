<script setup>
    import logo from '@/assets/img/logo.png'
    import {reactive} from 'vue'
    import {useRoute} from 'vue-router'

    const navs = reactive([
      {name:'Home',url:'/'},
      {name:'Jobs',url:'/jobs'},
      {name:'Add Job',url:'/jobs/add'}
    ])

    const isActiveLink = (routePath) => {
      const route = useRoute();
      return route.path === routePath;
    }
</script>
<template>
    <nav class="bg-green-700 border-b border-green-500">
      <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
        <div class="flex h-20 items-center justify-between">
          <div class="flex flex-1 items-center justify-center md:items-stretch md:justify-start">
            <!-- Logo -->
            <RouterLink
              class="flex flex-shrink-0 items-center mr-4" 
              to="/"
              >
              <img 
                class="h-10 w-auto" 
                :src="logo" 
                alt="Vue Jobs" />

              <span class="hidden md:block text-white text-2xl font-bold ml-2"
                >Shoppe</span
              >
            </RouterLink>
            <div class="md:ml-auto">
              <div class="flex space-x-2">
                <RouterLink 
                  v-for="nav in navs" :key="nav"
                  :to="`${nav.url}`"
                  :class="isActiveLink(`${nav.url}`) ? 'bg-green-900' : ' '"
                  class="text-white hover:bg-gray-900 hover:text-white rounded-md px-3 py-2"
                  >{{nav.name}}
                </RouterLink>
              </div>
            </div>

            <div class="md:ml-auto">
              <div class="flex space-x-2">
                <p class="text-white px-3 py-2">
                  <i class="pi pi-shopping-cart"></i>
                  Cart</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </nav>
</template>


<style scoped></style>