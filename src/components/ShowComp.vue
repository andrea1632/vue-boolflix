<template>
    <div class="container">
        <div class="row">
            <h2 class="text-uppercase text-center" v-if="show.length > 0">tv shows :</h2>
            <div class="col-3 cardBoolfix" v-for="elm, index in show" :key="index">
                <div>Titolo:{{elm.name}}</div>
                <div>Titolo originale: {{elm.original_name}}</div>
                <div>Voto: {{elm.vote_average}}</div>
                <div>Overview: {{elm.overview}}</div>
                <div class="d-flex justify-content-between">
                    <span>Lingua:</span>
                    <div class="flagContainer">
                        <img class="w-100" :src="whatFlag(elm)" alt="">
                    </div> 
                    
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ShowComp',
    props: {
        show: Array,
    },
    methods:{
        whatFlag(obj){
            if (obj.original_language == "en"){
                return "https://fastdatarecovery.com.au/wp-content/uploads/2021/06/UK-flag-union-jack-1024x6831-300x200-1.jpg"
            } else if(obj.original_language == "it"){
                return "https://m.media-amazon.com/images/I/21cWPlKRcQL._AC_SX450_.jpg"
            } else if(obj.original_language == "fr"){
                return "https://it.ejo.ch/wp-content/uploads/french-flag-1053711_640-300x200-1.png"
            } else if(obj.original_language == "es"){
                return "https://www.flagdetective.com/images/download/spain-state.jpg"
            } else if(obj.original_language == "nl"){
                return "https://cdn.horwathhtl.com/wp-content/uploads/sites/2/2018/01/Flag-of-Netherlands-300x200.gif"
            } else{
                return "https://e7.pngegg.com/pngimages/389/161/png-clipart-sign-symbol-x-mark-check-mark-christian-cross-symbol-miscellaneous-angle.png"
            }
        }
    }    
}
</script>

<style scoped>

</style>