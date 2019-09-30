<template>
  <div
    class="flex bg-blue-500 border-b border-gray-200 top-0 inset-x-0 z-100 h-16 items-center fixed z-40 shadow"
  >
    <div class="w-full max-w-screen-xl relative mx-auto px-6">
      <div class="flex items-center -mx-6">
        <div class="lg:w-1/4 xl:w-1/5 pl-6 pr-6 lg:pr-8">
          <div class="flex items-center">
            <span class="font-semibold text-xl tracking-tight text-white"
              >Property Listing</span
            >
          </div>
        </div>

        <div class="flex flex-grow lg:w-3/4 xl:w-4/5">
          <div class="w-full lg:px-6 xl:w-3/4 xl:px-12">
            <div class="relative">
              <span
                class="algolia-autocomplete"
                style="position: relative; display: inline-block; direction: ltr;"
                ><input
                  id="search"
                  v-model="searchStr"
                  class="transition focus:outline-0 border border-transparent focus:bg-white focus:border-gray-300 placeholder-gray-600 rounded-lg bg-gray-200 py-2 pr-4 pl-10 block w-full appearance-none leading-normal ds-input"
                  type="text"
                  placeholder="Title Search"
                  autocomplete="off"
                  spellcheck="false"
                  role="combobox"
                  aria-autocomplete="list"
                  aria-expanded="false"
                  aria-label="search input"
                  aria-owns="algolia-autocomplete-listbox-0"
                  style="position: relative; vertical-align: top;"
                  dir="auto"
                />
                <pre
                  aria-hidden="true"
                  style="position: absolute; visibility: hidden; white-space: pre; font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Helvetica Neue, Arial, Noto Sans, sans-serif, Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol, Noto Color Emoji; font-size: 16px; font-style: normal; font-variant: normal; font-weight: 400; word-spacing: 0px; letter-spacing: normal; text-indent: 0px; text-rendering: optimizelegibility; text-transform: none;"
                ></pre>
              </span>
              <div
                class="pointer-events-none absolute inset-y-0 left-0 pl-4 flex items-center"
              >
                <svg
                  class="fill-current pointer-events-none text-gray-600 w-4 h-4"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 20 20"
                >
                  <path
                    d="M12.9 14.32a8 8 0 1 1 1.41-1.41l5.35 5.33-1.42 1.42-5.33-5.34zM8 14A6 6 0 1 0 8 2a6 6 0 0 0 0 12z"
                  ></path>
                </svg>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    searchStr: {
      get() {
        return this.$store.getters.searchStr
      },
      set(val) {
        this.$store.commit('SET_SEARCH_STR', val)
      }
    }
  }
}
</script>
