<template>
    <div class="noticiar">    
        notícia:<h2>{{noticiaB_value.title}}</h2><br>
        Autor: {{noticiaB_value.by}}<br>
        Score: {{noticiaB_value.score}}<br>
        <input type="button" value="Descubra" v-on:click="apresentar">
    </div>
</template>

<script>
export default{
    name: "Noticiar",
    props: ["noticiaA", "noticiaB"],
    data(){
        return{
            noticiaA_value: "",
            noticiaB_value: "" 
        };
    },


    
    methods:{

        apresentar(){
            let posicao = this.noticiaA;
            let url="https://hacker-news.firebaseio.com/v0/item/"+posicao+".json?print=pretty";

            fetch(url)
                .then(res=>
                    {return res.json()
                    })
                    .then(elemento=>{
                        this.noticiaB_value=elemento})
        }

    }
};
</script>

<style scoped>

.noticiar{
    padding: 20px;
    width: 400px;
    box-shadow: 0 4px 8px 0 rgba(255, 253, 253, 0.2);
    height: 200px;
    margin: 0 auto;
}



</style>
