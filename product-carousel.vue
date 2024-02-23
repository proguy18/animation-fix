<template>
    <v-container>
        <v-row>
            <v-col v-if="carouselItems.length" cols="12" sm="12" md="6" lg="7" xl="8" class="custom-column-justify-center">
                <v-carousel
                    light
                    hide-delimiter-background
                    height="fit-content"
                    v-model="currentIndex"
                    :show-arrows="false"
                    class="custom-carousel-container"
                >
                    <v-carousel-item
                        v-for="(item, index) in carouselItems" :key="index"
                    >
                        <v-container class="container-carousel-img">
                            <img :src=item.src alt="LED TV" class="img-fluid carousel-img-item">
                        </v-container>
                    </v-carousel-item>
                </v-carousel>
                <v-slide-group
                    multiple
                    show-arrows
                    id="container-products-img-highlight"
                >
                    <v-slide-item
                        v-for="(item, index) in carouselItems"
                        :key="index"
                    >
                        <div class="custom-border-black">
                            <img :src=item.src alt="LED TV" class="img-fluid products-img-highlight-big pointer" v-if="currentIndex == item.id">
                            <img :src=item.src alt="LED TV" class="img-fluid products-img-highlight pointer" v-if="currentIndex != item.id" @click="changeSelectedItemCarousel(item.id)">
                        </div>
                    </v-slide-item>
                </v-slide-group>
                <!-- <v-container class="container-products-img-highlight">
                    <div class="custom-border-black" v-for="(item, index) in carouselItems" :key="index">
                        <img :src=item.src alt="LED TV" class="img-fluid products-img-highlight-big" v-if="currentIndex == item.id">
                        <img :src=item.src alt="LED TV" class="img-fluid products-img-highlight" v-if="currentIndex != item.id" @click="changeSelectedItemCarousel(item.id)">
                    </div>
                </v-container> -->
            </v-col>

            <v-col v-else cols="12" sm="12" md="6" lg="7" xl="8" class="custom-column-justify-center">
                <v-carousel
                    light
                    hide-delimiter-background
                    height="fit-content"
                    v-model="currentIndex"
                    :show-arrows="false"
                    class="custom-carousel-container"
                >
                    <v-carousel-item >
                        <v-container class="container-carousel-img">
                            <img src="/images/no_image.png" alt="LED TV" class="img-fluid carousel-img-item">
                        </v-container>
                    </v-carousel-item>
                </v-carousel>

                <v-slide-group
                    multiple
                    show-arrows
                    id="container-products-img-highlight"
                >
                    <v-slide-item >
                        <div class="custom-border-black">
                            <img src="/images/no_image.png" alt="LED TV" class="img-fluid products-img-highlight-big pointer" v-if="currentIndex == 0">
                        </div>
                    </v-slide-item>
                </v-slide-group>
            </v-col>

            <v-col cols="12" sm="12" md="6" lg="5" xl="4" class="custom-column-justify-center-default bg-test reset-pt">
                <v-container class="wrapper-products-text-carousel">
                    <v-container class="mt-pt-custom md-active mt-20px">
                        <!-- <h2 class="text-bolder">Mechanical</h2>
                        <h2 class="text-bolder">LED</h2> -->
                        <h2>{{ title }}</h2>
                    </v-container>
                    <v-container>
                        <!-- <div class="container-text-product-description">
                            <p>Artificial intelligence is the simulation of human intelligence processes by machines, especially computer systems. </p>
                        </div>
                        <div class="container-text-product-description mt-40px">
                            <p>Artificial intelligence is the simulation of human intelligence processes by machines, especially computer systems. </p>
                        </div> -->
                        <div class="container-text-product-description">
                            <p v-if="isDescriptionHide && glimpseText">{{ glimpseDescription }}</p>
                            <!-- <p v-else>{{ fullDescription }}</p> -->
                            <p v-html="fullDescription" v-else></p>
                        </div>
                    </v-container>
                </v-container>
                <v-container class="text-sign-minus-margin" v-if="glimpseText && isDescriptionHide" @click="toggleFullText">
                    <p id="text-sign">Read full Description</p>
                </v-container>
                <v-container class="text-sign-minus-margin-lg" v-if="!glimpseText" @click="toggleFullText">
                    <p id="text-sign">Hide Description</p>
                </v-container>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
    export default {
        name: 'ProductCarousel',
        props: {
            'carouselItems': Array,
            'title': String,
            'glimpseDescription': String,
            'fullDescription': String,
            'isDescriptionHide': Boolean,
        },
        data(){
            return {
                currentIndex: 0,
                textShowed: "",
                fullText: "",
                glimpseText: true,
            }
        },
        methods: {
            changeSelectedItemCarousel(itemId){
                this.currentIndex = itemId
            },
            toggleFullText(){
                this.glimpseText = !this.glimpseText;
            }
        },
        mounted () {
            const file = document.createElement('link');
            file.rel = 'stylesheet';
            file.href = "/css/carousel-products.css";
            document.head.appendChild(file);
        },
    }
</script>

<style scoped>
    .custom-carousel-container{
        display: flex;
        flex-direction: column !important;
        /* align-items: flex-end !important;
        justify-content: flex-end !important;
        align-content: flex-end !important; */
        align-items: center !important;
        justify-content: center !important;
        align-content: center !important;
        /* background-color: blue; */
    }

    .container-carousel-img{
        /* background-color: red; */
        height: 400px;
        width: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        align-content: center;
    }

    .custom-column-justify-center{
        display: flex;
        flex-wrap: wrap;
        flex-direction: column !important;
        align-content: center !important;
        align-items: center !important;
        /* background-color: coral; */
    }

    .custom-column-justify-center-default{
        display: flex;
        flex-wrap: wrap;
        justify-content: flex-start !important;
        align-content: flex-start !important;
        align-items: flex-start !important;
    }

    .reset-pt{
        padding-top: 0px !important;
    }

    /* .bg-test{
        background-color: yellow;
    } */

    .pointer{
        cursor: pointer;
    }

    .products-img-highlight{
        width: 30px;
        height: 30px;
    }

    .products-img-highlight-big{
        width: 70px;
        height: 70px;
    }

    /* .container-products-img-highlight{
        margin: 0px !important;
        padding: 0px !important;
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        cursor: pointer;
    } */

    #container-products-img-highlight{
        width: 70%;
    }

    .custom-border-black{
        border: 1px solid black;
        border-radius: 5px;
        margin: 5px;
        padding: 3px;
        height: fit-content;
    }

    .text-bolder{
        font-weight: 600;
    }

    .container-text-product-description{
        width: 350px;
        font-weight: 400;
    }

    .container-text-product-description p{
        margin: 0px !important;
        padding: 0px !important;
    }

    .mt-40px{
        margin-top: 40px !important;
    }

    .wrapper-products-text-carousel{
        margin-top: 20px;
        /* background-color: aqua; */
        /* height: 400px; */
        height: fit-content;
        overflow: hidden;
    }

    @keyframes changeToFullText {
        from {height: 350px;}
        to {height: 100%;}
    }

    .wrapper-products-text-carousel-full{
        padding-top: 20px !important;
        /* background-color: brown; */
        height: 100%;
        /* animation-name: changeToFullText;
        animation-duration: 5s;
        overflow: hidden; */
    }

    #text-sign{
        text-align: end;
        cursor: pointer;
        color: #2C80C9;
        text-decoration: underline;
    }

    .mt-pt-custom{
        margin-top: 20px !important;
        padding-top: 0px !important;
    }

    .carousel-img-item{
        border-radius: 15px;
        height: 90%;
        width: 100%;
    }

    .text-sign-minus-margin{
        margin-top: -30px !important;
    }

    .text-sign-minus-margin-lg{
        margin-top: -30px !important;
    }

    @media only screen and (max-width: 600px) {
        .products-img-highlight{
            width: 20px;
            height: 20px;
        }

        .products-img-highlight-big{
            width: 50px;
            height: 50px;
        }

        .custom-carousel-container{
            display: flex;
            flex-direction: column !important;
            align-items: center !important;
            justify-content: center !important;
            align-content: center !important;
            /* background-color: blue; */
        }

        #container-products-img-highlight{
            width: 100%;
        }

        .container-carousel-img{
            /* background-color: red; */
            height: 300px;
            width: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            align-content: center;
        }

        .reset-pt{
            margin-top: -12% !important;
        }
    }

    @media only screen and (max-width: 960px){
        .wrapper-products-text-carousel{
            margin-left: 0px !important;
        }

        .wrapper-products-text-carousel-full {
            margin-left: 0px !important;
        }

        .wrapper-products-text-carousel .md-active{
            text-align: center;
        }

        .wrapper-products-text-carousel-full .md-active{
            text-align: center;
        }

        .container-text-product-description{
            width: 70%;
            text-align: center;
            font-weight: 400;
            margin: auto;
        }

        .custom-carousel-container{
            display: flex;
            flex-direction: column !important;
            align-items: center !important;
            justify-content: center !important;
            align-content: center !important;
            /* background-color: blue; */
        }

        .reset-pt{
            margin-top: -3% !important;
        }

        #container-products-img-highlight{
            width: 100%;
        }
    }

    @media only screen and (max-width: 480px){
        .container-text-product-description{
            width: 100%;
            text-align: center !important;
            display: block;
            font-weight: 400;
        }
    }

    @media only screen and (min-width: 960px){
        .wrapper-products-text-carousel .md-active h2{
            text-align: left !important;
        }
    }
</style>
