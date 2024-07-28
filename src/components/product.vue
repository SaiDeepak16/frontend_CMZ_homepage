<template>
    <div class="border border-neutral-200 rounded-md hover:shadow-lg max-w-[300px]">
      <div class="relative">
        <SfLink href="#" class="block">
          <img
            :src="image"
            :alt="title"
            class="block object-cover h-auto rounded-md aspect-square"
            width="300"
            height="300"
          />
        </SfLink>
        <SfButton
          variant="tertiary"
          size="sm"
          square
          class="absolute bottom-0 right-0 mr-2 mb-2 bg-white ring-1 ring-inset ring-neutral-200 !rounded-full"
          aria-label="Add to wishlist"
        >
          <SfIconFavorite size="sm" />
        </SfButton>
      </div>
      <div class="p-4 border-t border-neutral-200">
        <SfLink href="#" variant="secondary" class="no-underline">{{ title }}</SfLink>
        <div class="flex items-center pt-1">
          <SfRating size="xs" :value="rating" :max="5" />
          <SfLink href="#" variant="secondary" class="pl-1 no-underline">
            <SfCounter size="xs">{{ reviews }}</SfCounter>
          </SfLink>
        </div>
        <span class="block pb-2 font-bold typography-text-lg">{{ price }}</span>
        <SfButton size="sm">
          <template #prefix>
            <SfIconShoppingCart size="sm" />
          </template>
          Add to cart
        </SfButton>
      </div>
    </div>
  </template>
  
  <script lang="ts" setup>
  import { defineProps } from 'vue';
  import { SfRating, SfCounter, SfLink, SfButton, SfIconShoppingCart, SfIconFavorite } from '@storefront-ui/vue';
  
  const props = defineProps({
    image: {
      type: String,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    rating: {
      type: Number,
      required: true
    },
    reviews: {
      type: Number,
      required: true
    },
    price: {
      type: String,
      required: true
    }
  });
  </script>
  