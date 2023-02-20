<template>
  <div class="stats__content">
    <b-row>
      <b-col>
        <StatsBox
          text="Total cars"
          iconType="grid"
          :data="total"
        />
      </b-col>
      <b-col>
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
</style>
