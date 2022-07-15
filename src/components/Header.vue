<template>
  <div
    class="w-full top-0 p-2 flex items-center justify-between py-4 px-6 bg-dark"
  >
    <div class="flex items-center">
      <button class="rounded-full bg-black w-8 h-8">
        <i class="fa-solid fa-angle-left" style="color: white"></i>
      </button>
      <button class="rounded-full bg-black w-8 h-8 ml-2">
        <i class="fa-solid fa-angle-right" style="color: white"></i>
      </button>
    </div>

    <div class="relative">
      <button
        @click="ShowDropDown = !ShowDropDown"
        class="bg-light rounded-full py-1 px-2 flex items-center"
      >
        <img src="../assets/prof.jpg" class="rounded-full h-6 w-6 mr-2" />
        <p class="text-white font-semibold text-xs mr-3">Kote</p>
        <i v-if="!ShowDropDown" class="fa-solid fa-angle-down text-white"></i>
        <i v-else class="fa-solid fa-angle-up text-white"></i>
      </button>

      <div v-if="ShowDropDown" class="absolute bg-light w-full rounded mt-1">
        <button
          class="py-2 text-lightest text-sm w-full hover:text-white border-b border-lightest"
        >
          Account
        </button>

        <button class="py-2 text-sm text-lightest w-full hover:text-white">
          Log out
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["ShowDropDown"],
};
</script>

<style></style>
