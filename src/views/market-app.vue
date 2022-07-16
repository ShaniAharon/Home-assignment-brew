<template>
  <main class="main-layout-container">
    <div class="my-list-container">
      <ul class="my-list links clean-list flex">
        <li>
          <a class="a-link"><span>Market Analysis</span></a>
        </li>
        <li>
          <a class="a-link"><span>Competitive Analysis</span></a>
        </li>
        <li>
          <a class="a-link plus-black"
            ><span><img src="../assets/plus-circle-icon.PNG" alt="" /></span
          ></a>
        </li>
      </ul>
    </div>
  </main>
  <section>
    <market-sort />
    <market-filter />
  </section>
  <div class="data-container main-layout-container flex g-2">
    <section class="block list-container">
      <div class="titles flex g-4">
        <h5>Number</h5>
        <h5>Title</h5>
      </div>
      <market-list @removed="removeMarket" v-if="markets" :markets="markets" />
    </section>
    <section class="block graph-container">
      <chart />
    </section>
  </div>
</template>

<script>
  import marketList from '../cmps/market-list.cmp.vue'
  import marketEdit from '../views/market-edit.vue'
  import marketDetails from '../views/market-details.vue'
  import marketFilter from '../cmps/market-filter.vue'
  import marketSort from '../cmps/market-sort.vue'
  import chart from '../cmps/chart.vue'

  export default {
    name: 'MarketApp',
    components: {
      marketList,
      marketEdit,
      marketFilter,
      marketDetails,
      marketSort,
      chart,
    },
    data() {
      return {}
    },
    methods: {
      removeMarket(marketId) {
        this.$store.dispatch({type: 'removeMarket', id: marketId})
      },
      setFilter(filterBy) {
        this.$store.dispatch({type: 'filter', filterBy})
      },
    },
    computed: {
      markets() {
        return this.$store.getters.markets
      },
    },
    unmounted() {},
  }
</script>
