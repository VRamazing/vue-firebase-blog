<template>

    <div id = "add-blog" >
    	<h2 >Add a new blog post</h2>
        <form v-if ="!submitted">

			<label>Blog Title: </label>
			<input v-model.lazy = "blog.title" name= "blog" type = "text"required/>

			<label>Blog Content:</label>
			<textarea v-model.lazy = "blog.content"></textarea>

            <div id="checkboxes">
                <label>Technology</label>
                <input v-model = "blog.categories" value= "Technology" type = "checkbox" required/>
                <label>Spiritual</label>
                <input v-model = "blog.categories" value= "Spiritual"  type = "checkbox"required/>
                <label>Life-lessons</label>
                <input v-model = "blog.categories" value= "Life-lessons"  type = "checkbox"required/>
                <label>Memoir</label>
                <input v-model = "blog.categories" value= "Memoir"  type = "checkbox"required/>
                <label>Experiment</label>
                <input v-model = "blog.categories" value= "Experiment"  type = "checkbox"required/>
            </div>

            <label>Author:</label>
            <select v-model="blog.author">
                <option v-for ="author in authors">{{author}}</option>
            </select>
            <button v-on:click.prevent = "post">Add Blog</button>

        </form>
        <div v-if ="submitted">
            <h3> Thanks for adding post</h3>
        </div>
        <div id = "preview">
        	<h3> Preview Blog: </h3>
        	<p>Blog title: {{blog.title}}</p>
        	<p>Blog content:</p>
            <p>{{blog.content}}</p>
            <p>Blog Categories :</p>
            <ul >
                <li v-for = "category in blog.categories">{{category}}</li>
            </ul>
            <p>Author: {{blog.author}}</p>
        </div>
    </div>

</template>

<script>

    export default {
        data(){
            return{
                blog : {
                    title : "",
                    content : "",
                    categories : [],
                    author:""
                },

                authors : ["Vignesh Ramesh","techieVignesh","VRamazing"],
                submitted : false

            }
        },
        methods : {
            post(){
                this.$http.post("https://vue-blog-acfa7.firebaseio.com/posts.json",this.blog).then(function(data){
                    console.log(data);
                    this.submitted = true;
                });
            }

        }
    }

</script>


<style scoped>
        #add-blog *{
        box-sizing: border-box;
    }
    #add-blog{
        margin: 20px auto;
        max-width: 500px;
    }
    label{
        display: block;
        margin: 20px 0 10px;
    }
    input[type="text"], textarea{
        display: block;
        width: 100%;
        padding: 8px;
    }
    #preview{
        padding: 10px 20px;
        border: 1px dotted #ccc;
        margin: 30px 0;
    }
    h3{
        margin-top: 10px;
    }
    #checkboxes input{
        display: inline-block;
        margin-right: 10px;
    }

    #checkboxes label{
        display:inline-block;
    }

</style>
