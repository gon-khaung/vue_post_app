<template>
    <div id="single-blog" class="single-blog">
        <h2>{{ blog.title }}</h2>
        <article>{{ blog.content }}</article>
    </div>
</template>

<script>
export default {
    data(){
        return{
            id:this.$route.params.id,
            blog:{}
        }
    },
    created(){
        this.$http.get('https://vue-postapp-netninja.firebaseio.com/posts/'+this.id+'.json').then(function(data){
            return data.json();
        }).then(function(data){
            this.blog = data;
        });
    }
}
</script>
<style scoped>
.single-blog{
    padding: 20px;
    margin: 20px 0;
    box-sizing: border-box;
    background: #eee;
}
</style>