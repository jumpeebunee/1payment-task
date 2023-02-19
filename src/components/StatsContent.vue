<template>
  <div class="stats__content">
    <b-row>
      <b-col>
        <div class="app__content stats__content-item">
          <div class="app__content-icon">
            <b-icon b-icon scale="0.5" icon="grid" class="rounded bg-primary p-1" variant="light"></b-icon>
          </div>
          <div>
            <p class="stats__content-description">Total cars</p>
            <h4>{{ total }}</h4>
          </div>
        </div>
      </b-col>
      <b-col>
        <div class="app__content stats__content-item">
          <div class="app__content-icon">
            <b-icon b-icon scale="0.5" icon="search" class="rounded bg-primary p-1" variant="light"></b-icon>
          </div>
          <div>
            <p class="stats__content-description">Car found</p>
            <h4>{{ finded }}</h4>
          </div>
        </div>
      </b-col>
    </b-row>
  </div>
</template>

<script>
  export default {
    props: ['total', 'finded'],
  }
</script>

<style scoped>
  .stats__content {
    margin-bottom: 20px;
  }

  .stats__content-description {
    margin-bottom: 0;
  }
  .stats__content-item {
    display: flex;
    gap: 10px;
  }
  .app__content-icon {
    font-size: 4rem;
    line-height: 0%;
  }
</style>
