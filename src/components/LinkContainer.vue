<template>
  <div
    class="w-3/4 h-3/4 bg-gray-500 border border-gray-200 rounded-lg flex items-center"
  >
    <div class="flex flex-col mx-auto w-[700px] gap-14">
      <div class="mb-8 space-y-3">
        <p class="text-4xl text-center font-extrabold">Link Shortener</p>
        <p class="text-white text-center text-xl">
          Shorten, Share, and Track Links Instantly with a URL Shortener
        </p>
      </div>
      <form>
        <div class="flex rounded-lg shadow-sm">
          <input
            type="text"
            id="hs-trailing-button-add-on"
            name="hs-trailing-button-add-on"
            placeholder="Place Your URL here..."
            class="py-3 px-4 w-full border-gray-200 shadow-sm rounded-s-full text-lg focus:z-10 focus:border-blue-500 focus:ring-blue-500 disabled:opacity-50 disabled:pointer-events-none placeholder:text-gray-500"
          />
          <button
            type="button"
            class="py-3 px-4 inline-flex w-[200px] justify-center items-center text-base font-semibold rounded-e-full border border-transparent bg-black text-white hover:bg-gray-800 focus:outline-none"
          >
            Shorten Link
          </button>
        </div>
        <div
          class="flex items-center mt-14 border-2 border-gray-600 bg-gray-400 w-max border-dashed mx-auto px-10 py-10 rounded-xl text-white gap-10"
        >
          <p class="text-xl font-bold text-black">Short link example</p>
          <button
            class="flex items-center gap-2 border-2 border-gray-600 bg-white/80 text-black font-bold rounded-xl py-2 px-3"
          >
            <img
              src="../assets/icons/copy_3914074.svg"
              alt="copy"
              width="20px"
            />
            Copy
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script setup></script>
