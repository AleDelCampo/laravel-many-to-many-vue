<script>
export default {
    name: 'AppFooter',
}

</script>

<template>
    <div class="container-fluid w-75 bg-jumbo rounded-3">
        <div class="jumbotron p-2 mb-4 bg-jumbo">
            <div class="container-fluid">
                <h1 class="display-4 fw-bold">Benvenuto!</h1>
                <p class="col-md-8 fs-4">Questa è la homepage del mio portfolio</p>
                <div>
                <router-link :class="my-btn" :to="{ name: 'contact-me' }" class="btn my-btn">Contattatemi</router-link>
            </div>
            </div>
            <!-- <a class="btn btn-light btn-lg text-uppercase fw-bold" href="{{ url('/dashboard') }}" role="button">Dashboard</a> -->
        </div>

    </div>
</template>

<style lang="scss" scoped>
div {
    color: black;
}

.bg-jumbo {
    background-color: #15f5ba;
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