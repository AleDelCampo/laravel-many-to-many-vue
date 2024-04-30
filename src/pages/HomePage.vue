<script>

import axios from 'axios';
export default {
    name: 'HomePage',
    data() {
        return {
        projects: [],

        apiLinks: [],
        apiPageNumber: 1,
        isLoading: true,
        baseApiUrl: 'http://127.0.0.1:8000/api',
        }
    },
    mounted() {
        
        this.apiCall();
    },
    methods: {

        apiCall() {

        this.isLoading = true
        axios.get(this.baseApiUrl + '/projects', {
            params: {
            page: this.apiPageNumber
            }
        }).then(res => {

            if(res.data.success) {

            this.isLoading = false
            }
            this.projects = res.data.results.data;
            this.apiLinks = res.data.results.links;
        })
        },
        changeApiPage(pageNumber) {
            
        this.apiPageNumber = pageNumber;
        this.apiCall();
        },
    },
}
</script>

<template>
  <div class="">

    <h1>I nostri Projects:</h1>

    <div v-if="!isLoading">

      <ul>
        <li v-for="project in projects" class="mb-2">
            {{ project.title }} <router-link :to="{name: 'single-project', params: {slug: project.slug}}" class="btn btn-outline-info btn-outline">Mostra</router-link>
        </li>
      </ul>

      <nav >
        <ul class="d-flex gap-2">

          <li v-for="link in apiLinks" v-html="link.label" @click="changeApiPage(link.label)" :class="link.label == apiPageNumber ? 'active' : ''">

          </li>

        </ul>      
      </nav>
    </div>
    <div v-else>
      <div class="spinner-border" role="status">
        <span class="visually-hidden">Loading...</span>
      </div>
    </div>

  </div>
</template>

<style lang="scss" scoped>
nav {
  margin-top: 100px;
  padding-top: 20px;
  border-top: solid 1px gray;
  ul {
    list-style-type: none;
    
    li {
      
      padding: 8px;
      text-decoration: none;
      color: white;
      transition: all .3s ease;
      cursor: pointer;
      &:hover, &.active {
        background-color: rgba(255,255,255,0.4);
        color: black;
      }
    }
  }
}
</style>