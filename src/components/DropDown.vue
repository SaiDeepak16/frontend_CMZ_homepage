<template>
    <div class="relative border border-neutral-200 rounded-md divide-y text-neutral-900">
      <SfAccordionItem
        v-for="({ id, summary, details }, index) in items"
        :key="id"
        :model-value="opened[index]"
        @update:model-value="updateOpened(index, $event)"
      >
        <template #summary>
          <span class="flex items-center cursor-pointer">
            <span class="whitespace-nowrap">{{ summary }}</span>
            <component
              :is="opened[index] ? SfIconExpandLess : SfIconExpandMore"
              class="ml-2"
            />
          </span>
        </template>
        <div v-if="opened[index]" class="absolute left-0 top-full mt-2 bg-white border border-neutral-200 rounded-md shadow-lg z-10 w-full">
          <div class="p-4 leading-10">
            <ul>
              <li v-for="(detail, detailIndex) in details" :key="detailIndex">
                <a :href="detail.url" class="text-black hover:underline hover:text-black">
                  {{ detail.name }}
                </a>
              </li>
            </ul>
          </div>
        </div>
      </SfAccordionItem>
    </div>
  </template>
  
  <script lang="ts" setup>
  import { SfAccordionItem, SfIconExpandMore, SfIconExpandLess } from "@storefront-ui/vue";
  import { ref } from "vue";
  
  const props = defineProps({
    items: {
      type: Array,
      required: true,
      default: () => [],
    },
  });
  
  const opened = ref<boolean[]>(props.items.map(() => false));
  
  const updateOpened = (index: number, value: boolean) => {
    opened.value = opened.value.map((state, idx) => (idx === index ? value : state));
  };
  </script>
  
  <style scoped>
  .relative .absolute {
    position: absolute;
  }
  </style>
  