<template>
    <div>
      <SfButton @click="toggleSidebar" class="lg:hidden order-first lg:order-1 mr-4" square variant="tertiary">
        <SfIconMenu />
      </SfButton>
  
      <transition name="slide">
        <div v-if="isOpen" class="fixed inset-0 bg-black bg-opacity-50 z-50">
          <div class="fixed top-0 left-0 w-64 h-full bg-white shadow-lg z-60 p-4 overflow-y-auto">
            <div class="flex justify-end">
              <SfButton @click="toggleSidebar" class="text-red-500" square variant="tertiary">
                <SfIconClose />
              </SfButton>
            </div>
            <nav>
              <ul>
                <li v-for="(item, index) in items" :key="index" class="mb-2">
                  <div v-if="item.subItems" class="relative">
                    <button @click="toggleSubMenu(index)" class="w-full text-left flex justify-between items-center text-primary-700 hover:underline">
                      {{ item.name }}
                      <SfIconExpandMore v-if="!isSubMenuOpen[index]" />
                      <SfIconExpandLess v-else />
                    </button>
                    <ul v-if="isSubMenuOpen[index]" class="pl-4 mt-2">
                      <li v-for="(subItem, subIndex) in item.subItems" :key="subIndex" class="mb-1">
                        <a :href="subItem.url" class="text-black hover:underline">{{ subItem.name }}</a>
                      </li>
                    </ul>
                  </div>
                  <div v-else>
                    <button @click="toggleSubMenu(index)" class="w-full text-left flex justify-between items-center text-primary-700 hover:underline">
                        <a :href="item.url" class="text-primary-700 hover:underline">{{ item.name }}</a>
                    </button>
                  </div>
                </li>
              </ul>
            </nav>
          </div>
        </div>
      </transition>
    </div>
  </template>
  
  <script lang="ts" setup>
  import { ref } from 'vue';
  import { SfButton, SfIconMenu, SfIconClose, SfIconExpandMore, SfIconExpandLess } from '@storefront-ui/vue';
  
  const props = defineProps({
    items: {
      type: Array,
      required: true,
      default: () => [],
    },
  });
  
  const isOpen = ref(false);
  const isSubMenuOpen = ref<boolean[]>([]);
  
  const toggleSidebar = () => {
    isOpen.value = !isOpen.value;
  };
  
  const toggleSubMenu = (index: number) => {
    isSubMenuOpen.value[index] = !isSubMenuOpen.value[index];
  };
  </script>
  
  <style scoped>
  .slide-enter-active, .slide-leave-active {
    transition: transform 0.3s ease;
  }
  .slide-enter, .slide-leave-to {
    transform: translateX(-100%);
  }
  </style>
  