<template>
  <section
    class="filter-container space-between main-layout-container flex align-center g-1"
  >
    <div class="filter-btn-container">
      <button class="filter-btn first-btn">filter button</button>
      <button class="filter-btn">filter button</button>
      <button class="filter-btn">filter button</button>
      <button class="filter-btn">filter button</button>
    </div>
    <div class="search flex align-center g-1">
      <img class="file-img" src="../assets/‏export-file-icon.png" alt="" />
      <input
        type="text"
        class="input-search"
        v-model="filterBy.label"
        placeholder="Search "
        @input="setFilter"
      />
    </div>
  </section>
</template>

<script>
  import {utilService} from '../services/util.service.js'
  export default {
    name: 'market-filter',
    data() {
      return {
        filterBy: {
          label: '',
        },
      }
    },
    created() {
      this.setFilter = utilService.debounce(this.setFilter, 400)
    },
    methods: {
      setFilter() {
        console.log(this.filterBy)
        this.$emit('setFilter', JSON.parse(JSON.stringify(this.filterBy)))
      },
    },
  }
</script>

<style></style>
