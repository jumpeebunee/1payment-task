<template>
  <div class="stats__content">
    <b-row class="stats__content__row">
      <b-col sm="6">
        <StatsBox
          text="Total cars"
          iconType="grid"
          :data="total"
        />
      </b-col>
      <b-col sm="6">
        <StatsBox
          text="Car found"
          iconType="search"
          :data="finded"
        />
      </b-col>
    </b-row>
  </div>
</template>

<script>
  import StatsBox from './StatsBox.vue';
  export default {
    props: ['total', 'finded'],
    components: { StatsBox },
  }
</script>

<style scoped>
  .stats__content {
    margin-bottom: 20px;
  }

  @media(max-width: 576px) {
    .stats__content__row {
      gap: 15px;
    }
  }
</style>
