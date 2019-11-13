<template>
    <div>
        <h1>Contact Page</h1>
        <div v-for="(item,index) in newsUpdate" :key="index">
            <h4>{{item.title}}</h4>
            <p class="author">{{item.author}}</p>
            <p class="cont">{{item.content}}</p>
            <p class="pub">{{item.publishedAt}}</p>
            <img :src= 'item.urlToImage'/>
        </div>
    </div>
</template>

<script>
export default {

data() {
return {
    newsUpdate: []
}
},
mounted() {
    this.$http.get('https://newsapi.org/v2/top-headlines?country=us&apiKey=84e9ab7c50914d08ba24c8d4060e62d8')
    .then(response=> {
        this.newsUpdate = response.data.articles;
    })
    .catch(error => {
        alert(error.response)
    })
},
};

</script>

<style scoped>
img {
    width: 400px;
    height: 300px;
}
</style>