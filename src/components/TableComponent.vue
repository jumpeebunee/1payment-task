<template>
  <div class="app__content app-table__content">
    <b-alert v-if="items.length === 0" variant="danger" show>There are no suitable cars</b-alert>
    <b-table 
      v-else
      head-variant="dark"
      hover 
      :items="items"
      :fields="fields"
      @sort-changed="sort"
    >
    </b-table>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        sortBy: '',
        sortOrder: false,
      }
    },
    props: ['fields', 'items'],
    methods: {
      sort(val) {
        const url = `https://localhost:3005/cars/index?sort=${val.sortBy}-${val.sortDesc ? 'DESC' : 'ASC'}`;
        console.log(url);
      }
    }
  }
</script>

<style scoped>

.app-table__content {
  border-top-left-radius: 0px;
  border-top-right-radius: 0px;
}
</style>
