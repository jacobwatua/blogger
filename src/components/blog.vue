<template>
  <div class="blog container" v-for="i in 5" :key="i">
    <div>
        <h4>Profile Owner</h4>
        <p>{{ user_name }}</p>
        <h4>Total Posts</h4>
        <p>{{ totalPosts }}</p>
        <h4>Featured Posts</h4>
        <p v-for="(post, i) in featuredPosts" :key="i"> - {{ post.title }}</p>
    </div>
  </div>
</template>

<script>
export default {
    data () {
        return {
            post : {
                fields : {
                    author : {
                        firstName : "Jacob",
                        lastName : "Watua",
                    },
                    entries : [
                        {
                            title : "When the sun goes down",
                            content : "Entry 1 content",
                            featured : true,
                        },
                        {
                            title : "Margins of Grace",
                            content : "Entry 2 content",
                            featured : false,
                        },
                        {
                            title : "On the run by Chinua Achebe",
                            content : "Murife don't run",
                            featured: true,
                        }
                    ],
                },
            }
        }
    },

    computed : {
        fullName () {
            return this.post.fields.author.firstName + " " + this.post.fields.author.lastName;
        },

        totalPosts () {
            return this.post.fields.entries.length;
        },

        featuredPosts () {
            return this.post.fields.entries.filter(entry=>{
                if (entry.featured){
                    return entry;
                }
            })
        },

        get user_name (){
            return this.fullName;
        }
    }
}
</script>

<style>
    .blog{
        box-shadow: 0px 1px 3px rgba(0, 0, 0, 0.2);
        border-radius: 8px;
        font-size: small;
        text-align: center;
        padding: 20px;
        margin: 50px auto;
        transition-property: background-color;
        transition-duration: .2s;
        transition-timing-function: ease-in-out;
        transition-delay: .2s;
        background-color: #ffffff;
    }
    p:hover {
        color:  orangered;
    }

    .blog:hover {
        background-color: lightgray;
    }
</style>