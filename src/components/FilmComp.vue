<template>
    <div class="container">
        <div class="row">
            <h2 class="text-uppercase py-4 text-center" v-if="films.length > 0">films :</h2>
            <div class="col cardBoolfix mb-5 justify-content-center d-flex" v-for="elm, index in films" :key="index">
                <!-- <div>Titolo:{{elm.title}}</div>
                <div>Titolo originale: {{elm.original_title}}</div>
                <div>Voto: {{elm.vote_average}}</div>
                <div>Overview: {{elm.overview}}</div>
                <div class="d-flex justify-content-between">
                    <span>Lingua:</span>
                    <div class="flagContainer">
                        <img class="w-100" :src="whatFlag(elm)" alt="">
                    </div>                     
                </div> -->
                <div class="flip-card">
                    <div class="flip-card-inner">
                        <div class="flip-card-front">
                            <img class="h-100" :src="`https://image.tmdb.org/t/p/w342${elm.poster_path}`" :alt="`poster of ${elm.original_title}`">
                        </div>
                        <div class="flip-card-back bg-dark p-5">
                            <div><strong>Titolo:</strong> {{elm.title}}</div>
                            <p> <strong>Titolo originale:</strong> {{elm.original_title}}</p>
                            <div>
                                <span class="me-3"><strong>Voto :</strong></span>
                                <span class="fs-2" :class="ceilVote(elm) > 1? 'text-warning' : ''">&#9733;</span>
                                <span class="fs-2" :class="ceilVote(elm) > 2? 'text-warning' : ''">&#9733;</span>
                                <span class="fs-2" :class="ceilVote(elm) > 3? 'text-warning' : ''">&#9733;</span>
                                <span class="fs-2" :class="ceilVote(elm) > 4? 'text-warning' : ''">&#9733;</span>
                                <span class="fs-2" :class="ceilVote(elm) >= 5? 'text-warning' : ''">&#9733;</span>
                            </div>
                            <div class="d-flex justify-content-between align-item-center py-2 px-4">
                                <span><strong>Lingua:</strong></span>
                                <div class="flagContainer">
                                    <img class="w-100" :src="whatFlag(elm)" alt="">
                                </div>
                            </div>
                            <p v-if="elm.overview != ''" class="text-start"><strong>Overview:</strong> {{elm.overview}}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'FilmComp',
        props: {
            films: Array,
        },
        methods: {
            whatFlag(obj) {
                if (obj.original_language == "en") {
                    return "https://fastdatarecovery.com.au/wp-content/uploads/2021/06/UK-flag-union-jack-1024x6831-300x200-1.jpg"
                } else if (obj.original_language == "it") {
                    return "https://m.media-amazon.com/images/I/21cWPlKRcQL._AC_SX450_.jpg"
                } else if (obj.original_language == "fr") {
                    return "https://it.ejo.ch/wp-content/uploads/french-flag-1053711_640-300x200-1.png"
                } else if (obj.original_language == "es") {
                    return "https://www.flagdetective.com/images/download/spain-state.jpg"
                } else if (obj.original_language == "nl") {
                    return "https://cdn.horwathhtl.com/wp-content/uploads/sites/2/2018/01/Flag-of-Netherlands-300x200.gif"
                } else {
                    return "https://e7.pngegg.com/pngimages/389/161/png-clipart-sign-symbol-x-mark-check-mark-christian-cross-symbol-miscellaneous-angle.png"
                }
            },
            ceilVote(obj){
                return Math.ceil(obj.vote_average / 2)
            }
        }
    }
</script>

<style>
    .flip-card {
        background-color: transparent;
        width: 342px;
        height: 512px;
        perspective: 1000px; /* 3D effect */
    }

    .flip-card-inner {
        position: relative;
        width: 100%;
        height: 100%;
        text-align: center;
        transition: transform 0.8s;
        transform-style: preserve-3d;
    }

    .flip-card:hover .flip-card-inner {
        transform: rotateY(180deg);
    }

    .flip-card-front,
    .flip-card-back {
        position: absolute;
        width: 100%;
        height: 100%;
        -webkit-backface-visibility: hidden;
        /* Safari */
        backface-visibility: hidden;
        overflow-y: auto;
        /* overflow: hidden; */
        overflow-x: hidden;
    }

    .flip-card-front {
        background-color: #bbb;
        color: black;
        border: 10px solid white;
    }

    .flip-card-back {
        color: white;
        transform: rotateY(180deg);
    }
</style>