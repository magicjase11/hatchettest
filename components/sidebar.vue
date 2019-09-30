<template>
  <div class="flex flex-col md:flex-row">
    <div
      class="h-full md:mt-12 md:w-48 md:fixed md:left-0 md:top-0 content-center md:content-start text-left justify-between"
    >
      <div class="h-full bg-gray-700">
        <div class="flex">
          <div class="w-1/6 mt-6 mb-3"></div>
          <div class="w-4/5 mt-6 mb-3">
            <div
              class="flex flex-wrap -mx-3 mb-2 bg-gray-600 p-2 rounded-sm mt-2"
            >
              <div class="w-full px-3 mb-6 md:mb-0">
                <label
                  class="block uppercase tracking-wide text-gray-200 text-xs font-bold mb-2"
                >
                  # Seats
                </label>
                <div class="relative">
                  <select
                    v-model="seats"
                    class="block appearance-none w-full bg-white border border-gray-200 text-gray-700 py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                  >
                    <option
                      v-for="option in $store.getters.allSeats"
                      :key="option.value"
                      :value="option.value"
                    >
                      {{ option.text }}
                    </option>
                  </select>
                  <div
                    class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700"
                  >
                    <svg
                      class="fill-current h-4 w-4"
                      xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 20 20"
                    >
                      <path
                        d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"
                      />
                    </svg>
                  </div>
                </div>
              </div>
            </div>

            <div
              class="flex flex-wrap -mx-3 mb-2 bg-gray-600 p-2 rounded-sm mt-2"
            >
              <div class="w-full px-3 mb-6 md:mb-0">
                <label
                  class="block uppercase tracking-wide text-gray-200 text-xs font-bold mb-2"
                >
                  Square Meters Low
                </label>
                <div class="relative">
                  <select
                    v-model="sqmLow"
                    class="block appearance-none w-full bg-white border border-gray-200 text-gray-700 py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                  >
                    <option
                      v-for="option in $store.getters.allMeters"
                      :key="option.value"
                      :value="option.value"
                    >
                      {{ option.text }}
                    </option>
                  </select>
                  <div
                    class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700"
                  >
                    <svg
                      class="fill-current h-4 w-4"
                      xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 20 20"
                    >
                      <path
                        d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"
                      />
                    </svg>
                  </div>
                </div>
              </div>
              <div class="w-full px-3 mb-6 md:mb-0">
                <label
                  class="block uppercase tracking-wide text-gray-200 text-xs font-bold mb-2"
                >
                  Square Meters High
                </label>
                <div class="relative">
                  <select
                    v-model="sqmHigh"
                    class="block appearance-none w-full bg-white border border-gray-200 text-gray-700 py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                  >
                    <option
                      v-for="option in $store.getters.allMeters"
                      :key="option.value"
                      :value="option.value"
                    >
                      {{ option.text }}
                    </option>
                  </select>
                  <div
                    class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700"
                  >
                    <svg
                      class="fill-current h-4 w-4"
                      xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 20 20"
                    >
                      <path
                        d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"
                      />
                    </svg>
                  </div>
                </div>
              </div>
            </div>

            <div
              class="flex flex-wrap -mx-3 mb-2 bg-gray-600 p-2 rounded-sm mt-2"
            >
              <div class="w-full px-3 mb-6 md:mb-0">
                <label
                  class="block uppercase tracking-wide text-gray-200 text-xs font-bold mb-2"
                >
                  Price Range Low
                </label>
                <div class="relative">
                  <select
                    v-model="priceLow"
                    class="block appearance-none w-full bg-white border border-gray-200 text-gray-700 py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                  >
                    <option
                      v-for="option in $store.getters.allPrices"
                      :key="option.value"
                      :value="option.value"
                    >
                      {{ option.text }}
                    </option>
                  </select>
                  <div
                    class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700"
                  >
                    <svg
                      class="fill-current h-4 w-4"
                      xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 20 20"
                    >
                      <path
                        d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"
                      />
                    </svg>
                  </div>
                </div>
              </div>
              <div class="w-full px-3 mb-6 md:mb-0">
                <label
                  class="block uppercase tracking-wide text-gray-200 text-xs font-bold mb-2"
                >
                  Price Range High
                </label>
                <div class="relative">
                  <select
                    v-model="priceHigh"
                    class="block appearance-none w-full bg-white border border-gray-200 text-gray-700 py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                  >
                    <option
                      v-for="option in $store.getters.allPrices"
                      :key="option.value"
                      :value="option.value"
                    >
                      {{ option.text }}
                    </option>
                  </select>
                  <div
                    class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700"
                  >
                    <svg
                      class="fill-current h-4 w-4"
                      xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 20 20"
                    >
                      <path
                        d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"
                      />
                    </svg>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="w-1/6 mt-6 mb-3"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    seats: {
      get() {
        return this.$store.getters.seats
      },
      set(val) {
        this.$store.commit('SET_SEATS', val)
      }
    },
    priceLow: {
      get() {
        return this.$store.getters.pricesLow
      },
      set(val) {
        this.$store.commit('SET_PRICES_LOW', val)
      }
    },
    priceHigh: {
      get() {
        return this.$store.getters.pricesHigh
      },
      set(val) {
        this.$store.commit('SET_PRICES_HIGH', val)
      }
    },
    sqmLow: {
      get() {
        return this.$store.getters.sqmsLow
      },
      set(val) {
        this.$store.commit('SET_SQMS_LOW', val)
      }
    },
    sqmHigh: {
      get() {
        return this.$store.getters.sqmsHigh
      },
      set(val) {
        this.$store.commit('SET_SQMS_HIGH', val)
      }
    }
  },
  methods: {}
}
</script>
<style></style>
