<template>
  <div class="app__content stats__content-item">
    <div class="app__content-icon">
      <b-icon b-icon scale="0.5" :icon="iconType" class="rounded bg-primary p-1" variant="light"></b-icon>
    </div>
    <div>
      <p class="stats__content-description">{{ text }}</p>
      <h4>{{ data }}</h4>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['text', 'data', 'iconType'],
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
