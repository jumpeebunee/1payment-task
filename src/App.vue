<template>
  <div id="app">
    <main>
      <section>
        <div class="container">
          <SortContent @updateQuery="changeQuery" @updateValue="changeValue" :value="value"/>
          <TableComponent
            :items="filteredAndRanged"
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
import SortContent from './components/SortContent';

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
      searchQuery: '',
      value: [2010, 2023],
    }
  },
  components: {TableComponent, SortContent},
  methods: {
    changeValue(val) {
      this.value = val;
    },
    changeQuery(val) {
      this.searchQuery = val;
    }
  },
  computed: {
    filteredItems() {
      let filtered;
      if (this.searchQuery) {
        filtered = this.items.filter(item => {
          return (
            item.id.toString().includes(this.searchQuery) ||
            item.brand.toLowerCase().includes(this.searchQuery.toLowerCase()) ||
            item.age.toString().includes(this.searchQuery)
          )
        })
      } else {
        filtered = this.items;
      }
      return filtered;
    },
    filteredAndRanged() {
      let filteredAndranged = this.filteredItems.filter(item => item.age > this.value[0] && item.age < this.value[1]);
      return filteredAndranged;
    }
  },
}
</script>

<style>
  #app {
    padding: 30px 0px;
    background-color: #F9FBFC;
  }
  .app__content {
    padding: 20px;
    border-radius: 6px;
    background-color: #fff;
    border: solid 1px #ECEEF0;
  }
  .app-sort__content {
    border-bottom-right-radius: 0px;
    border-bottom-left-radius: 0px;
  }

  .app-sort__range {
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .app__content-range {
    margin-top: 20px;
  }
</style>
<style src="@vueform/slider/themes/default.css"></style>