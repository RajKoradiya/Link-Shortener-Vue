<template>
  <div
    class="w-3/4 h-3/4 bg-gray-500 border border-gray-200 rounded-lg flex items-center"
  >
    <div class="flex flex-col mx-auto w-9/12 gap-14">
      <div class="mb-8 space-y-3">
        <p class="text-4xl text-center font-extrabold">Link Shortener</p>
        <p class="text-white text-center text-xl">
          Shorten, Share, and Track Links Instantly with a URL Shortener
        </p>
      </div>
      <form ref="formRef" @submit.prevent="onSubmit">
        <div class="flex rounded-lg shadow-sm">
          <input
            type="text"
            id="long-url"
            name="long-URL"
            v-model="longURL"
            placeholder="Place Your URL here..."
            class="py-3 px-4 w-full border-gray-200 shadow-sm rounded-s-full text-lg focus:z-10 focus:border-blue-500 focus:ring-blue-500 disabled:opacity-50 disabled:pointer-events-none placeholder:text-gray-500"
            ref="inputRef"
          />
          <button
            type="submit"
            class="py-3 px-4 inline-flex w-1/4 justify-center items-center text-base font-semibold rounded-e-full border border-transparent bg-black text-white hover:bg-gray-800 focus:outline-none"
          >
            Shorten Link
          </button>
        </div>
        <p class="text-red-600 text-sm font-bold ml-6 mt-2">{{ errorMSG }}</p>
        <div
          v-if="isShortURL"
          class="relative flex items-center mt-14 border-2 border-gray-600 bg-gray-400 w-max border-dashed mx-auto px-8 py-4 rounded-xl text-white gap-10"
        >
          <button
            class="absolute top-1 right-1 ml-5"
            @click="() => (isShortURL = false)"
          >
            <img
              src="../assets/icons/icons8-close.svg"
              alt="close"
              class="w-4 h-4"
            />
          </button>
          <img
            class="w-8 h-8 animate-spin"
            src="https://www.svgrepo.com/show/491270/loading-spinner.svg"
            alt="Loading icon"
            v-if="!isResponce"
          />
          <div v-if="isResponce" class="flex items-center gap-10">
            <p class="text-base font-medium text-black" id="short-url">
              {{ shortURL ? shortURL : "short url...." }}
            </p>
            <button
              type="button"
              class="btn flex items-center gap-1 border-2 border-gray-600 bg-white/80 text-black font-bold rounded-xl py-1 px-2 text-xs active:shadow-md active:text-gray-500"
              :data-clipboard-text="longURL"
              @click="copyURL"
            >
              <img
                src="../assets/icons/copy_3914074.svg"
                alt="copy"
                width="15px"
              />
              Copy
            </button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script setup>
import ClipboardJS from "clipboard";
import { computed, onMounted, ref, watch } from "vue";

const formRef = ref();
const isShortURL = ref(false);
const inputRef = ref();
const shortURL = ref("");
const longURL = ref("");
const errorMSG = ref("");

onMounted(() => {
  inputRef.value.focus();
});

const isResponce = computed(() => (isShortURL.value ? true : false));

watch(longURL, () => {
  if (longURL.value) {
    errorMSG.value = "";
  } else {
    errorMSG.value = "URL Requeired!!!";
  }
});

const onSubmit = () => {
  if (inputRef.value.value !== "") {
    // const formData = new FormData(formRef.value);
    // longURL.value = inputRef.value.value;
    const id = generateUniqueIDforShortURL();
    shortURL.value = `https://short.ly/${id}`;
    isShortURL.value = true;
  } else {
    errorMSG.value = "URL Requeired!!!";
  }
};

const copyURL = () => {
  const clipboard = new ClipboardJS(".btn");

  clipboard.on("success", (e) => {
    e.clearSelection();
  });
};

function generateUniqueIDforShortURL() {
  const charSet = process.env.VUE_APP_CHARSET;
  const length = 12;

  let gnid = "";
  for (let i = 0; i < length; i++) {
    gnid += charSet[Math.floor(Math.random() * charSet.length)];
  }

  return gnid;
}
</script>
