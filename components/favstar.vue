<template>
  <a href="javascript:void(0);" @click="handleFav()"
    ><svg
      :class="{
        'fav-icon-selected': favedLocal,
        'fav-icon-unselected': !favedLocal
      }"
      class="fav-icon inline-block h-12 w-12"
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 40 20"
    >
      <polygon
        id="Star-3"
        points="10 15 4.12214748 18.0901699 5.24471742 11.545085 0.489434837 6.90983006 7.06107374 5.95491503 10 0 12.9389263 5.95491503 19.5105652 6.90983006 14.7552826 11.545085 15.8778525 18.0901699"
      ></polygon></svg
  ></a>
</template>

<script>
export default {
  props: {
    faved: {
      type: Boolean,
      required: false,
      deafult: false
    }
  },
  computed: {
    favedLocal: {
      get() {
        return this.faved
      },
      set(val) {
        this.$emit('update:faved', val)
      }
    }
  },
  methods: {
    handleFav() {
      this.favedLocal = !this.favedLocal
    }
  }
}
</script>
<style>
.fav-icon:hover {
  fill: yellow !important;
}

.fav-icon-selected {
  fill: yellow;
  stroke: black;
}

.fav-icon-unselected {
  fill: black;
  stroke: black;
}
</style>
