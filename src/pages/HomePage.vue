<script>
import axios from 'axios';
import AppHeader from '../components/AppHeader.vue';
import {store} from '../store.js';

import AppJumbo from '../components/AppJumbo.vue';

export default {
  name: 'HomePage',

  components: {
    AppHeader,
    AppJumbo
  },

  data() {
    return {
      store,
      apiLinks: [],
      apiPageNumber: 1,
      isLoading: true,
      baseApiUrl: 'http://127.0.0.1:8000/api',
      currentPage: 1,
    };
  },

  mounted() {
    this.apiCall();
  },

  methods: {
    apiCall() {
      this.isLoading = true;
      axios.get(this.baseApiUrl + '/projects', {
        params: {
          page: this.apiPageNumber
        }
      }).then(res => {
        if (res.data.success) {
          this.isLoading = false;
        }
        store.projects = res.data.results.data;
        store.filteredProjects = store.projects;
        this.apiLinks = res.data.results.links;
      });
    },

    changeApiPage(pageUrl) {
      this.isLoading = true;
      axios.get(pageUrl)
        .then(response => {
          store.projects = response.data.results.data;
          store.filteredProjects = store.projects;
          this.apiLinks = response.data.results.links;
          this.isLoading = false;
        });
    },
    
    setCurrentPage(pageNumber) {
      this.currentPage = pageNumber;
    },
    
   
  }
}
</script>

<template>
  <AppJumbo></AppJumbo>

  <div class="container w-75 text-black">

    <h1>I miei Progetti:</h1>

    <div v-if="!isLoading">

      <ul>
        <li v-for="project in store.filteredProjects" :key="project.slug" class="mb-2">
          {{ project.title }} <router-link :to="{ name: 'single-project', params: { slug: project.slug } }"
            class="btn my-btn">Mostra</router-link>
        </li>
      </ul>

      <nav>
        <ul class="d-flex gap-2">
          <li v-if="apiLinks.prev_page_url">
            <button @click="changeApiPage(apiLinks.prev_page_url); setCurrentPage(currentPage - 1)">Previous</button>
          </li>

          <li v-for="link in apiLinks" :key="link.url" v-html="link.label"
            @click="changeApiPage(link.url); setCurrentPage(link.label)" :class="{ active: link.label == currentPage }">
          </li>

          <li v-if="apiLinks.next_page_url">
            <button @click="changeApiPage(apiLinks.next_page_url); setCurrentPage(currentPage + 1)">Next</button>
          </li>
        </ul>
      </nav>
    </div>
    <div v-else>
      <div class="spinner-border" role="status">
        <span class="visually-hidden">Loading....</span>
      </div>
    </div>

  </div>
</template>

<style lang="scss" scoped>
nav {
  padding-top: 20px;
  border-top: solid 1px #211951;

  ul {
    list-style-type: none;

    li {

      padding: 8px;
      text-decoration: none;
      color: black;
      transition: all .4s ease;
      cursor: pointer;

      &:hover,
      &.active {
        background-color: rgba(255, 255, 255, 0.4);
        color: black;
      }
    }
  }
}

.my-btn {
  border: 1px solid #fd2bfd;
  color: #fd2bfd;

  &:hover {
    background-color: #fd2bfd;
    color: black;
  }

}
</style>