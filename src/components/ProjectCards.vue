<script>
export default {

  name: 'ProjectCards',

  props: {
    project: Object,
  },

  data() {

    return {

    }
  },

  mounted() {

  },

  methods: {


  },
}
</script>

<template>

  <div class="card container-fluid w-25 bg-pj">
    <img class="card-img-top mt-2 img-size" :src="'http://127.0.0.1:8000/storage/' + project.image" alt="Copertina">
    <div class="card-body">
      <h2 class="card-title">{{ project.title }}</h2>
      <p class="card-text">{{ project.description }}</p>
      <div v-if="project.type">
        <small>{{ project.type.title }}</small>
      </div>
      <div class="d-flex mt-2 gap-2">
        <div v-for="technology in project.technologies" :key="technology.id">
          <img class="icon-size" :src="'http://127.0.0.1:8000/storage/' + technology.preview" alt="Tecnologia">
        </div>
      </div>
    </div>
  </div>

</template>

<style lang="scss" scoped>

.bg-pj {
  background-color: #15f5ba;
}

div {
  color: black;
}

</style>