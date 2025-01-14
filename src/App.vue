<script setup>
import Container from "./components/Container.vue";
import * as icons from "@adersolutions/icons";
import { iconMetadata } from "./iconMetadata";
import { ref, computed } from "vue";
// Reactive search query
const copyStatus = ref("");
const searchQuery = ref("");

// Computed property to filter icons
const filteredIcons = computed(() => {
  const query = searchQuery.value.toLowerCase();
  if (!query) return iconMetadata;

  return iconMetadata.filter((icon) => {
    const { name, keywords, description } = icon;

    // Check if the query matches the name, any keyword, or the description
    return (
      name.toLowerCase().includes(query) ||
      keywords.some((keyword) => keyword.toLowerCase().includes(query)) ||
      description.toLowerCase().includes(query)
    );
  });
});
const copyText = async (value) => {
  if (value.trim() === "") {
    copyStatus.value = "Please enter some text to copy.";
    return;
  }

  try {
    await navigator.clipboard.writeText(value); // Using Clipboard API
    copyStatus.value = "Text copied successfully!";
  } catch (error) {
    copyStatus.value = "Failed to copy text.";
  }
  setTimeout(() => {
    copyStatus.value = "";
  }, 3000);
};
</script>
<template>
  <Container >

    <div class="grid grid-cols-1 w-full max-w-screen-md mx-auto ">
      <input
        class="col-start-1 row-start-1 h-12 w-full pl-11 pr-4 text-base text-white outline-none placeholder:text-gray-200 sm:text-sm bg-white/10 rounded-lg"
        v-model="searchQuery"
        placeholder="Search icons..."
      />

      <component :is="icons['SearchIcon']" class="pointer-events-none col-start-1 row-start-1 ml-4 size-5 self-center text-gray-400"/>
    </div>
    <ul class="max-w-screen-md mx-auto grid grid-cols-5 gap-4 mt-5 min-h-80 pb-20">
      <li v-for="(item, idx) in filteredIcons" :key="idx" class="flex flex-col justify-center items-center gap-2 p-1 bg-gray-900 border border-white/10 rounded-lg shadow-sm cursor-pointer opacity-100 hover:opacity-70 active:scale-95 transition-all overflow-hidden" @click="copyText(item.name)">
        <component :is="icons[item.name]" class="w-8 text-white" />
        <p class="text-[10px] text-gray-300 truncate max-w-32">{{ item.name }}</p>
      </li>
    </ul>
    <div v-if="copyStatus" class="fixed bottom-0 inset-x-0 bg-white text-black text-center  p-2 m-2 rounded-lg">
      {{ copyStatus }}
    </div>
  </Container>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
