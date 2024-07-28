<template>
    <div class="flex items-center justify-center overflow-x-auto p-4 space-x-10 lg:space-x-50">
      <div
        v-for="(category, index) in categories"
        :key="index"
        class="flex flex-col items-center max-w-[50px] sm:max-w-[50px] md:max-w-[50px] lg:max-w-[100px] hover:cursor-pointer"
      >
        <img :src="category.image" alt="Category Image" class="rounded-lg w-full h-auto">
        <p class="text-sm mt-2">{{ category.name }}</p>
      </div>
    </div>
  </template>
  
  
  <script>
export default {
  data() {
    return {
      categories: [
        { name: 'Essentials', image: 'https://storage.googleapis.com/sfui_docs_artifacts_bucket_public/production/display-2.png' },
        { name: 'Uniforms', image: 'https://storage.googleapis.com/sfui_docs_artifacts_bucket_public/production/display-3.png' },
        { name: 'Clothing', image: 'https://storage.googleapis.com/sfui_docs_artifacts_bucket_public/production/display.png' },
        // Add more categories as needed
      ]
    };
  }
};
</script>