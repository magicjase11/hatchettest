<template>
  <div class="text-gray-900 leading-normal">
    <div id="header"><Nav /></div>

    <div class="container mx-auto sm:ml-56">
      <div class="header-padded"></div>

      <Sidebar />

      <div
        v-if="propertyArr.length === 0"
        class="bg-blue-100 border-t mt-8 border-b border-blue-500 text-blue-700 px-4 py-3"
        role="alert"
      >
        <p class="font-bold">No Results</p>
        <p class="text-sm">
          We Could not find any listings matching your criteria.
        </p>
      </div>

      <div v-else>
        <div
          v-for="(propertyRow, indexii) in propertyArr"
          :key="indexii"
          class="flex flex-wrap -mx-1 overflow-hidden sm:-mx-1 md:-mx-px lg:-mx-1 xl:-mx-1"
        >
          <div
            v-for="(property, indexjj) in propertyRow.data"
            :key="indexjj"
            class="my-1 px-1 w-full overflow-hidden sm:my-1 sm:px-1 md:my-px md:px-px md:w-full lg:my-1 lg:px-1 lg:w-1/3 xl:my-1 xl:px-1 xl:w-1/3"
          >
            <!-- Column Content -->
            <Card
              v-if="property != undefined"
              :created-at="property.created_at"
              :title="property.title"
              :price-p-m="property.price_per_month"
              :seats="property.seats"
              :sqm="property.sqm"
              :image="property.profile_image"
              :desc="property.description"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// https://tailwindgrids.com/#/

import Nav from '~/components/nav.vue'
import Card from '~/components/card.vue'
import Sidebar from '~/components/sidebar.vue'

export default {
  components: {
    Nav,
    Card,
    Sidebar
  },
  computed: {
    propertyArr: {
      get() {
        const filteredArr = []
        const finalArr = []
        for (let ii = 0; ii < this.$store.getters.fakeData.length; ii++) {
          const curTitle = this.$store.getters.fakeData[ii].title
          if (
            this.searchFilter(this.$store.getters.searchStr, curTitle) &&
            this.applyRangeFilters(this.$store.getters.fakeData[ii])
          ) {
            filteredArr.push(this.$store.getters.fakeData[ii])
          }
        }

        for (let ii = 0; ii < filteredArr.length; ii += 3) {
          finalArr.push({
            data: [filteredArr[ii], filteredArr[ii + 1], filteredArr[ii + 2]]
          })
        }

        return finalArr
      }
    }
  },
  methods: {
    searchFilter(inSearch, inTitle) {
      let isOK = false
      if (inSearch === '' || inSearch === null || inSearch === undefined) {
        isOK = true
      } else if (inTitle.toLowerCase().includes(inSearch.toLowerCase())) {
        isOK = true
      }

      return isOK
    },
    applyRangeFilters(inData) {
      let passes = true

      if (inData !== undefined) {
        if (this.$store.getters.seats > 0) {
          if (inData.seats !== this.$store.getters.seats) {
            passes = false
          }
        }

        if (this.$store.getters.pricesLow > 0) {
          if (inData.price_per_month < this.$store.getters.pricesLow) {
            passes = false
          }
        }

        if (this.$store.getters.pricesHigh > 0) {
          if (inData.price_per_month > this.$store.getters.pricesHigh) {
            passes = false
          }
        }

        if (this.$store.getters.sqmsLow > 0) {
          if (inData.sqm < this.$store.getters.sqmsLow) {
            passes = false
          }
        }

        if (this.$store.getters.sqmsHigh > 0) {
          if (inData.sqm > this.$store.getters.sqmsHigh) {
            passes = false
          }
        }
      }

      return passes
    }
  }
}
</script>

<style>
.header-padded {
  padding-top: 4em;
}
</style>
