<script lang="ts" setup>
const alpine = useAppConfig().alpine;

const show = ref(false);
</script>

<template>
  <header
    :class="alpine.header?.position || 'left'"
    class="relative grid grid-cols-12 items-center gap-4 py-16"
  >
    <div class="menu absolute right-0 flex hover:text-purple-500 sm:hidden">
      <button aria-label="Navigation Menu" @click="show = !show">
        <svg
          width="24"
          height="24"
          viewBox="0 0 68 68"
          fill="currentColor"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M8 34C8 32.1362 8 31.2044 8.30448 30.4693C8.71046 29.4892 9.48915 28.7105 10.4693 28.3045C11.2044 28 12.1362 28 14 28C15.8638 28 16.7956 28 17.5307 28.3045C18.5108 28.7105 19.2895 29.4892 19.6955 30.4693C20 31.2044 20 32.1362 20 34C20 35.8638 20 36.7956 19.6955 37.5307C19.2895 38.5108 18.5108 39.2895 17.5307 39.6955C16.7956 40 15.8638 40 14 40C12.1362 40 11.2044 40 10.4693 39.6955C9.48915 39.2895 8.71046 38.5108 8.30448 37.5307C8 36.7956 8 35.8638 8 34Z"
          />
          <path
            d="M28 34C28 32.1362 28 31.2044 28.3045 30.4693C28.7105 29.4892 29.4892 28.7105 30.4693 28.3045C31.2044 28 32.1362 28 34 28C35.8638 28 36.7956 28 37.5307 28.3045C38.5108 28.7105 39.2895 29.4892 39.6955 30.4693C40 31.2044 40 32.1362 40 34C40 35.8638 40 36.7956 39.6955 37.5307C39.2895 38.5108 38.5108 39.2895 37.5307 39.6955C36.7956 40 35.8638 40 34 40C32.1362 40 31.2044 40 30.4693 39.6955C29.4892 39.2895 28.7105 38.5108 28.3045 37.5307C28 36.7956 28 35.8638 28 34Z"
          />
          <path
            d="M48 34C48 32.1362 48 31.2044 48.3045 30.4693C48.7105 29.4892 49.4892 28.7105 50.4693 28.3045C51.2044 28 52.1362 28 54 28C55.8638 28 56.7956 28 57.5307 28.3045C58.5108 28.7105 59.2895 29.4892 59.6955 30.4693C60 31.2044 60 32.1362 60 34C60 35.8638 60 36.7956 59.6955 37.5307C59.2895 38.5108 58.5108 39.2895 57.5307 39.6955C56.7956 40 55.8638 40 54 40C52.1362 40 51.2044 40 50.4693 39.6955C49.4892 39.2895 48.7105 38.5108 48.3045 37.5307C48 36.7956 48 35.8638 48 34Z"
          />
        </svg>
      </button>
    </div>

    <div
      class="overlay absolute right-0 top-28 rounded-md border-2 border-solid border-gray-200 bg-gray-100 p-6 text-right text-lg font-medium leading-8 backdrop-blur-md transition-all will-change-auto dark:border-gray-800 dark:bg-gray-900 sm:hidden"
      :class="[show && 'show']"
    >
      <MainNav @link-click="show = !show" />
    </div>

    <div
      class="logo col-span-12 flex h-12 text-3xl font-extrabold sm:col-span-4 sm:col-start-auto"
    >
      <NuxtLink v-if="alpine.header?.logo" to="/">
        <h1 class="hover:text-purple-200">Rohit Prakash</h1>
      </NuxtLink>
    </div>

    <div
      class="main-nav hidden sm:col-span-8 sm:flex sm:justify-end sm:text-xl sm:font-medium sm:leading-6"
    >
      <MainNav />
    </div>
  </header>
</template>

<style scoped lang="ts">
css({
  header: {
    '.overlay': {
      '&:not(.show)': {
        opacity: 0,
        transform: 'translateY(-10px) rotateY(-8deg) rotateX(-20deg)',
        pointerEvents: 'none'
      },
    },
  }
})
</style>
