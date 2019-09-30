<template>
  <div class="max-w-sm rounded overflow-hidden shadow-lg">
    <img class="w-full h-48" :src="image" :alt="title + ' Image'" />
    <div class="px-6 py-4">
      <div class="font-bold text-xl mb-2">
        {{ title }}

        <FavStar :faved.sync="favSelected" />
      </div>

      <p class="text-gray-700 text-base">
        {{ maxChars(desc, 130) }}
      </p>
    </div>
    <div class="px-6 py-4">
      <p class="text-gray-700 text-base"><b>Price:</b> {{ pricePM }}</p>
      <p class="text-gray-700 text-base"><b>Square Meters:</b> {{ sqm }}</p>
      <p class="text-gray-700 text-base"><b>Seats:</b> {{ seats }}</p>
    </div>
    <div class="px-6 py-4 bg-gray-300">
      <button
        class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full"
        @click="handleSelection(title)"
      >
        View Listing
      </button>
    </div>
  </div>
</template>

<script>
import FavStar from '~/components/favstar.vue'

export default {
  components: {
    FavStar
  },
  props: {
    createdAt: {
      type: String,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    pricePM: {
      type: Number,
      required: true
    },
    seats: {
      type: Number,
      required: true
    },
    sqm: {
      type: Number,
      required: true
    },
    image: {
      type: String,
      required: true
    },
    desc: {
      type: String,
      required: true
    }
  },
  computed: {
    favSelected: {
      get() {
        if (
          this.$store.getters.favSelected[this.title + this.createdAt] ===
          undefined
        ) {
          return false
        } else {
          return this.$store.getters.favSelected[this.title + this.createdAt]
        }
      },
      set(val) {
        this.$store.commit('SET_FAV_DATA', this.title + this.createdAt)
      }
    }
  },
  methods: {
    maxChars(inStr, maxLen) {
      let newStr = ''
      if (inStr.length > maxLen) {
        newStr = inStr.substr(0, maxLen) + '...'
      } else {
        newStr = inStr
      }
      return newStr
    },
    handleSelection(title) {
      this.$router.push('#/' + title)
    }
  }
}
</script>
