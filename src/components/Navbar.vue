<template>
  <header
    class="flex justify-center w-full py-2 px-4 lg:py-5 lg:px-6 bg-white border-b border-neutral-200"
  >
    <div
      class="flex flex-wrap lg:flex-nowrap items-center flex-row justify-start h-full max-w-[1536px] w-full"
    >
      <SidebarMenu :items="menuItems" />
      <a
        href="#"
        aria-label="SF Homepage"
        class="inline-block mr-4 focus-visible:outline focus-visible:outline-offset focus-visible:rounded-sm shrink-0"
      >
        <picture>
          <source srcset="../images/logo.png" media="(min-width: 768px)" />
          <img
            src="../images/logo2.png"
            alt="Sf Logo"
            class="w-15 h-8 lg:w-[8rem] lg:h-[3rem] md:w-[8rem] md:h-[3rem]"
          />
        </picture>
      </a>
      <SfButton
        class="hidden lg:mr-4"
        type="button"
        variant="tertiary"
        @click="toggleIcon"
      >
      </SfButton>
      <DropDown 
        class="hidden lg:flex lg:mr-4 p-2 hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-primary-500"
        type="button"
        variant="tertiary" 
        :items="accordionItems"
      />
      <form
        role="search"
        class="flex flex-[100%] order-last lg:order-3 mt-2 lg:mt-0 pb-2 lg:pb-0"
        @submit.prevent="search"
      >
        <SfInput
          v-model="inputValue"
          type="search"
          class="[&::-webkit-search-cancel-button]:appearance-none"
          placeholder="Search"
          wrapper-class="flex-1 h-10 pr-0"
          size="base"
        >
          <template #suffix>
            <span class="flex items-center">
              <SfButton
                variant="tertiary"
                square
                aria-label="search"
                type="submit"
                class="rounded-l-none hover:bg-transparent active:bg-transparent"
              >
                <SfIconSearch />
              </SfButton>
            </span>
          </template>
          <template #input>
            <input
              v-model="inputValue"
              type="search"
              placeholder="Search"
              list="itemOptions"
              class="w-full h-full border-0 outline-none"
            />
          </template>
        </SfInput>
        <datalist id="itemOptions">
          <option v-for="item in itemOptions" :key="item" :value="item">{{ item }}</option>
        </datalist>
      </form>
      <nav class="flex-1 flex justify-end lg:order-last lg:ml-4">
        <div class="flex flex-row flex-nowrap">
          <SfButton
            v-for="actionItem in actionItems"
            :key="actionItem.ariaLabel"
            class="mr-2 -ml-0.5 rounded-md text-primary-700 hover:bg-primary-100 active:bg-primary-200 hover:text-primary-600 active:text-primary-700"
            :aria-label="actionItem.ariaLabel"
            variant="tertiary"
            square
          >
            <template #prefix>
              <Component :is="actionItem.icon" />
            </template>
            <span
              v-if="actionItem.role === 'login'"
              class="hidden xl:inline-flex whitespace-nowrap"
              >{{ actionItem.label }}</span
            >
          </SfButton>
        </div>
      </nav>
    </div>
  </header>
</template>

<script lang="ts" setup>
import DropDown from "../components/DropDown.vue";
import SidebarMenu from "./SidebarMenu.vue";
import { ref } from "vue";
import {
  SfButton,
  SfIconShoppingCart,
  SfIconFavorite,
  SfIconPerson,
  SfIconExpandMore,
  SfIconExpandLess,
  SfInput,
  SfIconSearch,
  SfIconMenu,
} from "@storefront-ui/vue";

const menuItems = [
  { name: 'Home', url: '/' },
  { name: 'Products', subItems: [
    { name: 'Accessories', url: '/products/accessories' },
    { name: 'Uniforms', url: '/products/uniforms' },
    { name: 'Essentials', url: '/products/essentials' },
  ]},
  { name: 'About Us', url: '/about' },
  { name: 'Contact', url: '/contact' },
];

const actionItems = [
  {
    icon: SfIconShoppingCart,
    ariaLabel: "Cart",
    role: "button",
    label: "",
  },
  {
    icon: SfIconFavorite,
    ariaLabel: "Wishlist",
    role: "button",
    label: "",
  },
  {
    label: "Log in",
    icon: SfIconPerson,
    ariaLabel: "Log in",
    role: "login",
  },
];

const inputValue = ref("");
const itemOptions = ref([
  "Ahmedabad",
  "Delhi",
  "Dehradun",
  "Mumbai",
  "Bangalore",
  "Jaipur",
  "Baroda",
  "Chennai"
]);

const search = () => {
  alert(`Search triggered for: ${inputValue.value}`);
};

const accordionItems = ref([
  {
    id: 'acc-1',
    summary: 'Browse Products',
    details: [
      { name: 'Essentials', url: '/track-order' },
      { name: 'Uniforms', url: '/delivery-info' },
      { name: 'Accessories', url: '/shipping-rates' },
    ],
  },
]);
</script>

<style scoped>
/* Add any additional styles here */
</style>
