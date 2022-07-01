<template>
    <div class="page">
        <div class="p-5 bg-dark text-light">
            <div class="container d-flex justify-content-between">
                <div class="ms-3">
                    <h1 class="display-3">Ops! Page not found, 404</h1>
                    <p class="lead">Sorry the page you're loking for doesn't exist</p>
                </div>
                <img src="https://picsum.photos/200" alt="">

            </div>
        </div>
        <div class="container py-5">

            This page doesn't exist. Go back to:
                <ul class="mt-2">
                    <li>
                        <router-link :to="{name:'home'}" >HomePage</router-link>

                    </li>
                    <li>
                        <router-link :to="{name:'about'} " >About</router-link>

                    </li>
                    <li>
                        <router-link :to="{name:'posts'}" >Posts</router-link>

                    </li>
                </ul>

        </div>


    </div>

</template>

<script>
export default {
   neme: 'NotFound'
}
</script>


<style lang="scss" scoped>

</style>