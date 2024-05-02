<script>
import axios from 'axios';

export default{
    name: 'Error404',
    data(){
        return{
            baseApiUrl: 'http://127.0.0.1:8000/api',
        }
    }
}
</script>

<template>
    <div class="container">
        <div class="d-flex flex-column align-items-center justify-content-center" style="min-height: 80vh;">
        <h1 class="text-center my-5 display-1 fw-bold">404</h1>
        <h4>Oops! Hai incontrato un errore.</h4>
        <p class="text-muted">La pagina che stai cercando non è stata trovata.</p>
    </div>
    </div>
</template>
