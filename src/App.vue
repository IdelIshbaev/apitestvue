<template>
  <div id="app">
    <FilteredPostsList v-model="keyWord" :results="filteredSearchResults" :onlineResults="onlineSearch" @click="search"/>  
    <Loader v-if="loader"/>
  </div>
</template>

<script>
import FilteredPostsList from "./components/FilteredPostsList";
import Loader from "./components/Loader";

export default {
  name: "App",
  data: () => ({
    posts: [],
    filteredSearchResults: [],
    keyWord: '',
    loader: true
  }),
  components: {
    FilteredPostsList,
    Loader
  },
  created() {
    this.init(); 
    // setTimeout(() => {this.init()}, 1000); // to check loader
  },
  methods: {
     init() {
      fetch('https://jsonplaceholder.typicode.com/posts')
        .then(response => response.json())
        .then(json => {
          this.posts = json
          this.filteredSearchResults = this.posts
          this.loader = false
        })
    },
    search() {
      this.filteredSearchResults = this.posts.filter(item => {
        return item.title.toLowerCase().includes(this.keyWord.toLowerCase());
        });
    }
  },
  computed: {
    onlineSearch() {
      return this.posts.filter(item => {
        return item.title.toLowerCase().includes(this.keyWord.toLowerCase());
        });
    }
  }
};
</script>