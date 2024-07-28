<template>
    <div class="flex flex-wrap gap-4 lg:gap-6 lg:flex-nowrap justify-center p-5">
      <div
        v-for="({ icon, title, description, isDisabled }, index) in cardDetails"
        :key="`${title}-${index}`"
        class="flex flex-col w-full max-w-[325px] sm:w-[375px] lg:w-[496px] items-center border border-solid border-gray-400 rounded-lg py-8 px-1"
      >
        <component :is="icon" size="2xl" :class="{ 'text-disabled-900': isDisabled }" />
        <div class="p-4 flex flex-col items-center">
          <p :class="['font-medium typography-text-base', { 'text-disabled-900': isDisabled }]">{{ title }}</p>
          <p
            :class="[
              'mt-1 mb-4 font-normal typography-text-sm text-neutral-700 text-center',
              { 'text-disabled-700': isDisabled },
            ]"
          >
            {{ description }}
          </p>
        </div>
      </div>
    </div>
  </template>
  <script lang="ts" setup>
  import { SfIconPackage, SfIconWarehouse, SfIconSell } from '@storefront-ui/vue';
  
  const cardDetails = [
    {
      icon: SfIconPackage,
      title: 'Free shipping',
      description: 'Learn about our commitments to ethics, our team, our communities and more.',
      buttonText: 'Read more',
    },
    {
      icon: SfIconWarehouse,
      title: 'Click & Collect',
      description: 'Learn about our commitments to ethics, our team, our communities and more.',
      buttonText: 'Read more',
    },
    {
      icon: SfIconSell,
      title: 'Affordable Prices',
      description: 'Learn about our commitments to ethics, our team, our communities and more.',
      buttonText: 'Read more',
    },
  ];
  </script>
  
  