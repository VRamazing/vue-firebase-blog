<template>

    <div>
       <app-header></app-header>
       <router-view></router-view>
        

    </div>

</template>


<script>
    import addBlog from './components/addBlog.vue'
    import showBlogs from './components/showBlogs.vue'
    import listBlogs from './components/listBlogs.vue'
    import header from './components/header.vue'



    export default {
        components:{
            'add-blog': addBlog,
            'show-blog': showBlogs,
            'list-blog': listBlogs,
            'app-header': header,


        }
    }

</script>


<style >
    body{
        margin: 0;
        /*padding:0;*/
    }
    h1{color:violet;}

</style>
