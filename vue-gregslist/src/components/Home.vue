<template>
    <div>
        <h1>Vue is fun</h1>
        <button @click="createNewBlog">CREATE</button>
        <div v-if="blogs.length > 0">
            <ul>
                <li v-for="blog in blogs">
                    <router-link :to="{name: 'Blog', params: {blogId: blog._id}}">{{blog.title}}</router-link>
                </li>
            </ul>
        </div>
        <div v-else>
            <img src="https://media.tenor.com/images/85d269dc9595a7bcf87fd0fa4039dd9f/tenor.gif" alt="">
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
            }
        },
        computed:{
            blogs(){
                return this.$store.state.blogs
            }
        },
        methods:{
            createNewBlog(){
                var newBlog = {
                    title: "A NEW BLOG",
                    body: "YOU GET A BLOG"
                }
                this.$store.dispatch("createBlog", newBlog)
            }
        },
        mounted(){
            this.$store.dispatch("getBlogs")
        }

    }

</script>

<style></style>