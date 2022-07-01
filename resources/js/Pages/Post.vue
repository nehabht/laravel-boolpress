<template>
  <div class="single_page h-100">
        <div class="wrapper h-100" v-if="!loading">
            <div class="p-5 hero_image" :style="{backgroundImage: 'url(/storage/' + post.image + ')'}"></div>
            <div class="container">
                <h1 class="display-3">{{ post.title }}</h1>
                <p class="lead">{{ post.body}}</p>
                <hr class="my-2 bg-white" />
                <div class="row">
                    <div class="col" v-if="post.category">
                        <strong>Category: </strong> {{ post.category.name }}
                    </div>
                    <div class="col" v-if="post.tags.length > 0">
                        <strong>Tags: </strong>
                        <span v-for="tag in post.tags" :key="tag.id">
                            #{{ tag.name }}
                        </span>
                    </div>
                </div>
            </div>
        </div>
        <div class="loading bg-dark text-center text-white" v-else>
            Loading...
        </div>
    </div>

</template>

<script>
export default {
  name: "Post",
  data() {
    return {
      post: "",
      loading: true,
    };
  },
  methods: {
    getPost() {
      axios
        .get("/api/posts/" + this.$route.params.slug)
        .then((response) => {
          console.log(response);

          if (response.data.status_code === 404) {
            console.log('404 page not found');
            this.$router.push({ name: 'not-found'});
            
          } else {
            console.log('page found')
            this.post = response.data;
            this.loading = false;
          }
        })
        .catch((e) => {
          console.error(e);
        });
    },
  },
  mounted() {
    this.getPost();
  },
};
</script>

<style lang="scss" scoped>

</style>