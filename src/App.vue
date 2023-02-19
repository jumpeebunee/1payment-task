<template>
  <div id="app">
    <main>
      <section>
        <div class="container">
          <TableComponent
            :items="items"
            :fields="fields"
          />
        </div>
      </section>
    </main>
  </div>
</template>

<script>
import { data } from './data/data';
import TableComponent from './components/TableComponent';

export default {
  name: 'App',
  data() {
    return {
      fields: [
        { key: 'id', sortable: true },
        { key: 'brand', sortable: true },
        { key: 'age', sortable: true },
      ],
      items: data,
    }
  },
  components: {TableComponent,},

}
</script>

<style>
  #app {
    background-color: #F9FBFC;
  }
  .app__content {
    padding: 20px;
    border-radius: 20px;
    background-color: #fff;
    border: solid 1px #ECEEF0;
  }
</style>
