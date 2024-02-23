<template>
    <v-skeleton-loader
        :loading="loading"
        min-height="100vh"
        width="100vw"
        type="image"
        transition="slide-y-transition"
    >
        <section
            class="learn-more-container"
            v-if="$vuetify.breakpoint.smAndDown"
        >
            <v-container id="first-column">
                <v-carousel
                    height="fit-content"
                    :show-arrows="false"
                    hide-delimiter-background
                >
                    <v-carousel-item>
                        <v-container class="center-vertically">
                            <v-container class="small-box">
                                <v-img
                                    :src="img_card_1"
                                    aspect-ratio="1"
                                ></v-img>
                                <v-container class="description-box">
                                    <h3 v-html="title_card_1"></h3>
                                    <p v-html="description_card_1"></p>
                                    <div class="button-content-container">
                                        <button class="learnmore-button">
                                            {{ button_card_1 }}
                                            <i
                                                class="fas fa-angle-right custom-icons-home"
                                            ></i>
                                        </button>
                                    </div>
                                </v-container>
                            </v-container>
                        </v-container>
                    </v-carousel-item>
                    <v-carousel-item>
                        <v-container
                            class="center-vertically">
                            <div class="container-outer-spinner">
                                <div id="spin">
                                    <v-img
                                        :src="url_current_hassle"
                                        class="img-marker"
                                        aspect-ratio="1"
                                    ></v-img>
                                    <div class="marker"></div>
                                </div>
                                <div class="container-spinner" ref="circle">
                                    <div
                                        class="product clickable"
                                        @click="productClicked"
                                        id="productText"
                                    >
                                        <div
                                            :class="[
                                                !this.product_clicked
                                                    ? 'black-layer'
                                                    : 'hidden',
                                            ]"
                                        ></div>
                                        <curve-text
                                            :height="70"
                                            class="text-field"
                                            :r="40"
                                            >{{ spinner_text_1 }}</curve-text
                                        >
                                    </div>
                                    <div
                                        class="maintenance clickable"
                                        @click="maintenanceClicked"
                                    >
                                        <div
                                            :class="[
                                                !this.maintenance_clicked
                                                    ? 'black-layer'
                                                    : 'hidden',
                                            ]"
                                        ></div>
                                        <curve-text
                                            :height="70"
                                            class="text-field"
                                            :r="40"
                                            >{{ spinner_text_2 }}</curve-text
                                        >
                                    </div>
                                    <div
                                        class="manage-service clickable"
                                        @click="manageServiceClicked"
                                        id="manageService"
                                    >
                                        <div
                                            :class="[
                                                !this.manage_service_clicked
                                                    ? 'black-layer'
                                                    : 'hidden',
                                            ]"
                                        ></div>
                                        <curve-text
                                            :height="70"
                                            class="text-field"
                                            :r="40"
                                            >{{ spinner_text_3 }}</curve-text
                                        >
                                    </div>
                                    <div
                                        class="install clickable"
                                        @click="installClicked"
                                    >
                                        <div
                                            :class="[
                                                !this.install_clicked
                                                    ? 'black-layer'
                                                    : 'hidden',
                                            ]"
                                        ></div>
                                        <curve-text
                                            :height="70"
                                            class="text-field"
                                            :r="40"
                                            >{{ spinner_text_4 }}</curve-text
                                        >
                                    </div>
                                </div>
                            </div>
                            <v-container class="medium-box-outer">
                                <v-container class="medium-box">
                                    <v-container class="description-box">
                                        <h3
                                            class="text-center"
                                            v-html="title_card_4"
                                        ></h3>
                                        <p
                                            class="text-center"
                                            v-html="description_card_4"
                                        ></p>
                                        <div class="button-content-container">
                                            <button class="learnmore-button">
                                                {{ button_card_4 }}
                                                <i
                                                    class="fas fa-angle-right custom-icons-home"
                                                ></i>
                                            </button>
                                        </div>
                                    </v-container>
                                </v-container>
                            </v-container>
                        </v-container>
                    </v-carousel-item>
                </v-carousel>
            </v-container>

            <v-container id="second-column" v-if="ready" class="mt-med">
                <v-carousel
                    height="fit-content"
                    :show-arrows="false"
                    hide-delimiter-background
                >
                    <v-carousel-item>
                        <v-container class="big-box">
                            <v-container
                                class="outer-video"
                                :key="rerender_key"
                            >
                                <video
                                    autoplay
                                    :loop="true"
                                    muted
                                    id="video-section-1"
                                >
                                    <source
                                        :src="video_card_2"
                                        type="video/mp4"
                                    />
                                </video>
                            </v-container>
                            <v-container class="description-box">
                                <h3 v-html="title_card_2"></h3>
                                <p v-html="description_card_2"></p>
                                <div class="button-content-container">
                                    <button class="learnmore-button">
                                        {{ button_card_2 }}
                                        <i
                                            class="fas fa-angle-right custom-icons-home"
                                        ></i>
                                    </button>
                                </div>
                            </v-container>
                        </v-container>
                    </v-carousel-item>
                    <v-carousel-item>
                        <v-container class="big-box">
                            <v-img
                                :src="img_card_3"
                                aspect-ratio="1"
                                class="border-img"
                            ></v-img>
                            <v-container class="description-box">
                                <h3 v-html="title_card_3"></h3>
                                <p v-html="description_card_3"></p>
                                <div class="button-content-container">
                                    <button class="learnmore-button">
                                        {{ button_card_3 }}
                                        <i
                                            class="fas fa-angle-right custom-icons-home"
                                        ></i>
                                    </button>
                                </div>
                            </v-container>
                        </v-container>
                    </v-carousel-item>
                </v-carousel>
            </v-container>
        </section>

        <section class="learn-more-container" v-else>
            <v-container id="first-column" v-if="ready">
                <v-container class="center-vertically">
                    <v-container class="small-box">
                        <v-img :src="img_card_1" aspect-ratio="1"></v-img>
                        <v-container class="description-box">
                            <h3 v-html="title_card_1"></h3>
                            <p v-html="description_card_1"></p>
                            <div class="button-content-container">
                                <button class="learnmore-button">
                                    {{ button_card_1 }}
                                    <i
                                        class="fas fa-angle-right custom-icons-home"
                                    ></i>
                                </button>
                            </div>
                        </v-container>
                    </v-container>
                </v-container>
                <v-container class="big-box">
                    <v-container class="outer-video" :key="rerender_key">
                        <video autoplay :loop="true" muted id="video-section-1">
                            <source :src="video_card_2" type="video/mp4" />
                        </video>
                    </v-container>
                    <v-container class="description-box">
                        <h3 v-html="title_card_2"></h3>
                        <p v-html="description_card_2"></p>
                        <div class="button-content-container">
                            <button class="learnmore-button">
                                {{ button_card_2 }}
                                <i
                                    class="fas fa-angle-right custom-icons-home"
                                ></i>
                            </button>
                        </div>
                    </v-container>
                </v-container>
            </v-container>
            <v-container id="second-column" v-if="ready" class="mt-med">
                <v-container class="big-box">
                    <v-img
                        :src="img_card_3"
                        aspect-ratio="1"
                        class="border-img"
                    ></v-img>
                    <v-container class="description-box">
                        <h3 v-html="title_card_3"></h3>
                        <p v-html="description_card_3"></p>
                        <div class="button-content-container">
                            <button class="learnmore-button">
                                {{ button_card_3 }}
                                <i
                                    class="fas fa-angle-right custom-icons-home"
                                ></i>
                            </button>
                        </div>
                    </v-container>
                </v-container>
                <v-container class="center-vertically mt-min">
                    <div class="container-outer-spinner">
                        <div id="spin">
                            <v-img
                                :src="url_current_hassle"
                                class="img-marker"
                                aspect-ratio="1"
                            ></v-img>
                            <div class="marker"></div>
                        </div>
                        <div class="container-spinner" ref="circle">
                            <div
                                class="product clickable"
                                @click="productClicked"
                                id="productText"
                            >
                                <div
                                    :class="[
                                        !this.product_clicked
                                            ? 'black-layer'
                                            : 'hidden',
                                    ]"
                                ></div>
                                <curve-text
                                    :height="70"
                                    class="text-field"
                                    :r="40"
                                    >{{ spinner_text_1 }}</curve-text
                                >
                            </div>
                            <div
                                class="maintenance clickable"
                                @click="maintenanceClicked"
                            >
                                <div
                                    :class="[
                                        !this.maintenance_clicked
                                            ? 'black-layer'
                                            : 'hidden',
                                    ]"
                                ></div>
                                <curve-text
                                    :height="70"
                                    class="text-field"
                                    :r="40"
                                    >{{ spinner_text_2 }}</curve-text
                                >
                            </div>
                            <div
                                class="manage-service clickable"
                                @click="manageServiceClicked"
                                id="manageService"
                            >
                                <div
                                    :class="[
                                        !this.manage_service_clicked
                                            ? 'black-layer'
                                            : 'hidden',
                                    ]"
                                ></div>
                                <curve-text
                                    :height="70"
                                    class="text-field"
                                    :r="40"
                                    >{{ spinner_text_3 }}</curve-text
                                >
                            </div>
                            <div
                                class="install clickable"
                                @click="installClicked"
                            >
                                <div
                                    :class="[
                                        !this.install_clicked
                                            ? 'black-layer'
                                            : 'hidden',
                                    ]"
                                ></div>
                                <curve-text
                                    :height="70"
                                    class="text-field"
                                    :r="40"
                                    >{{ spinner_text_4 }}</curve-text
                                >
                            </div>
                        </div>
                    </div>
                    <v-container class="medium-box-outer">
                        <v-container class="medium-box">
                            <v-container class="description-box">
                                <h3
                                    class="text-center"
                                    v-html="title_card_4"
                                ></h3>
                                <p
                                    class="text-center"
                                    v-html="description_card_4"
                                ></p>
                                <div class="button-content-container">
                                    <button class="learnmore-button">
                                        {{ button_card_4 }}
                                        <i
                                            class="fas fa-angle-right custom-icons-home"
                                        ></i>
                                    </button>
                                </div>
                            </v-container>
                        </v-container>
                    </v-container>
                </v-container>
            </v-container>
        </section>
    </v-skeleton-loader>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import CurveText from "@inotom/vue-curve-text";

gsap.registerPlugin(ScrollTrigger);

export default {
    components: {
        CurveText,
    },
    props: {
        dynamicContent: {
            type: Object,
            required: true,
        },
    },
    data() {
        return {
            spinner_at: 1,
            url_hassle:
                this.dynamicContent.img_spinner_1 &&
                this.dynamicContent.img_spinner_2 &&
                this.dynamicContent.img_spinner_3 &&
                this.dynamicContent.img_spinner_4
                    ? [
                          this.dynamicContent.img_spinner_1,
                          this.dynamicContent.img_spinner_2,
                          this.dynamicContent.img_spinner_3,
                          this.dynamicContent.img_spinner_4,
                      ]
                    : [
                          "/img/hassle/hassle-product.png",
                          "/img/hassle/hassle-maintenance.png",
                          "/img/hassle/hassle-manage-service.png",
                          "/img/hassle/hassle-install.png",
                      ],
            url_current_hassle: this.dynamicContent.img_spinner_1
                ? this.dynamicContent.img_spinner_1
                : "/img/hassle/hassle-product.png",
            product_clicked: true,
            maintenance_clicked: false,
            manage_service_clicked: false,
            install_clicked: false,
            title_card_1: this.dynamicContent.title_card_1
                ? this.dynamicContent.title_card_1
                : `<span class="text-bolder">Maximize</span> Revenue`,
            title_card_2: this.dynamicContent.title_card_2
                ? this.dynamicContent.title_card_2
                : `<span class="text-bolder">Optimize</span> Your Business Operation`,
            title_card_3: this.dynamicContent.title_card_3
                ? this.dynamicContent.title_card_3
                : `<span class="text-bolder">Stand Out</span> In Your Industry`,
            title_card_4: this.dynamicContent.title_card_4
                ? this.dynamicContent.title_card_4
                : `Hassle-<span class="text-bolder">Free</span>`,
            description_card_1: this.dynamicContent.description_1
                ? this.dynamicContent.description_1
                : "Discover untapped revenue potential through our advanced analytics",
            description_card_2: this.dynamicContent.description_2
                ? this.dynamicContent.description_2
                : "Leverage our data insights to unlock efficiency gains and cost-saving opportunities",
            description_card_3: this.dynamicContent.description_3
                ? this.dynamicContent.description_3
                : "Stay ahead of the curve and set your business apart with our customized creative solutions. Create out-of-the-box solutions to effectively achieve your objective.",
            description_card_4: this.dynamicContent.description_4
                ? this.dynamicContent.description_4
                : "We handle it all, from installation to maintenance, allowing you to stay focused on what you do best",
            button_card_1: this.dynamicContent.button_text_1
                ? this.dynamicContent.button_text_1
                : "More",
            button_card_2: this.dynamicContent.button_text_2
                ? this.dynamicContent.button_text_2
                : "More",
            button_card_3: this.dynamicContent.button_text_3
                ? this.dynamicContent.button_text_3
                : "More",
            button_card_4: this.dynamicContent.button_text_4
                ? this.dynamicContent.button_text_4
                : "More",
            img_card_1: this.dynamicContent.img_url_1
                ? this.dynamicContent.img_url_1
                : "/img/maximize-revenue.png",
            video_card_2: this.dynamicContent.video_url_1
                ? this.dynamicContent.video_url_1
                : "video/cctv-store-tracking.mp4",
            img_card_3: this.dynamicContent.img_url_2
                ? this.dynamicContent.img_url_2
                : "/img/stand-out-industry.jpg",
            spinner_text_1: this.dynamicContent.spinner_text_1
                ? this.dynamicContent.spinner_text_1
                : "Product",
            spinner_text_2: this.dynamicContent.spinner_text_2
                ? this.dynamicContent.spinner_text_2
                : "Maintenance",
            spinner_text_3: this.dynamicContent.spinner_text_3
                ? this.dynamicContent.spinner_text_3
                : "Manage Service",
            spinner_text_4: this.dynamicContent.spinner_text_4
                ? this.dynamicContent.spinner_text_4
                : "Install",
            ready: false,
            loading: true,
            rerender_key: 1,
        };
    },
    watch: {
        dynamicContent(newVal, _) {
            if (newVal.button_text_1) {
                this.button_card_1 = newVal.button_text_1;
            }

            if (newVal.button_text_2) {
                this.button_card_2 = newVal.button_text_2;
            }

            if (newVal.button_text_3) {
                this.button_card_3 = newVal.button_text_3;
            }

            if (newVal.button_text_4) {
                this.button_card_4 = newVal.button_text_4;
            }

            if (newVal.title_card_1) {
                this.title_card_1 = newVal.title_card_1;
            }

            if (newVal.title_card_2) {
                this.title_card_2 = newVal.title_card_2;
            }

            if (newVal.title_card_3) {
                this.title_card_3 = newVal.title_card_3;
            }

            if (newVal.title_card_4) {
                this.title_card_4 = newVal.title_card_4;
            }

            if (newVal.description_1) {
                this.description_card_1 = newVal.description_1;
            }

            if (newVal.description_2) {
                this.description_card_2 = newVal.description_2;
            }

            if (newVal.description_3) {
                this.description_card_3 = newVal.description_3;
            }

            if (newVal.description_4) {
                this.description_card_4 = newVal.description_4;
            }

            if (newVal.img_url_1) {
                this.img_card_1 = newVal.img_url_1;
            }

            if (newVal.img_url_2) {
                this.img_card_3 = newVal.img_url_2;
            }

            if (newVal.video_url_1) {
                this.video_card_2 = newVal.video_url_1;
                this.rerender_key++;
            }

            if (newVal.spinner_text_1) {
                this.spinner_text_1 = newVal.spinner_text_1;
            }

            if (newVal.spinner_text_2) {
                this.spinner_text_2 = newVal.spinner_text_2;
            }

            if (newVal.spinner_text_3) {
                this.spinner_text_3 = newVal.spinner_text_3;
            }

            if (newVal.spinner_text_4) {
                this.spinner_text_4 = newVal.spinner_text_4;
            }

            if (
                newVal.img_spinner_1 &&
                newVal.img_spinner_2 &&
                newVal.img_spinner_3 &&
                newVal.img_spinner_4
            ) {
                this.url_current_hassle = newVal.img_spinner_1;
                this.url_hassle.length = 0;
                this.url_hassle.push(newVal.img_spinner_1);
                this.url_hassle.push(newVal.img_spinner_2);
                this.url_hassle.push(newVal.img_spinner_3);
                this.url_hassle.push(newVal.img_spinner_4);
            }

            // this.ready = true;
            // this.loading = false;
        },
    },
    mounted() {
        const file = document.createElement("link");
        file.rel = "stylesheet";
        file.href = "/css/curved-text-learn-more.css";
        const secondFile = document.createElement("link");
        secondFile.rel = "stylesheet";
        secondFile.href = "/css/skeleton-loader.css";
        document.head.appendChild(file);
        document.head.appendChild(secondFile);

        const carousel = document.createElement('link');
        carousel.rel = "stylesheet",
        carousel.href = "/css/carousel-news.css",
        document.head.appendChild(carousel);

        this.ready = true;
        this.loading = false;

        // // Top Cards
        // gsap.to(
        //     ".security-card-container-top h2, .security-card-container-top p, .security1-button, .ai-card-container-top h2, .ai-card-container-top p, .ai1-button",
        //     {
        //         y: "-13.5vh",
        //         ease: "bounceIn",
        //         scrollTrigger: {
        //             trigger: ".ai-card-container-top",
        //             start: "top bottom",
        //             end: "center center",
        //             scrub: 2,
        //             // markers: true,
        //             once: true,
        //         },
        //     }
        // );

        // // Card 3
        // gsap.to(
        //     ".ai-card-container-bottom h2, .ai-card-container-bottom p, .ai2-button",
        //     {
        //         y: "-13.5vh",
        //         ease: "bounceIn",
        //         scrollTrigger: {
        //             trigger: ".ai-card-container-bottom",
        //             start: "top bottom",
        //             end: "center center",
        //             scrub: 2,
        //             // markers: true,
        //             once: true,
        //         },
        //     }
        // );

        // // Card 4
        // gsap.to(".security-card-container-bottom h2, .security2-button", {
        //     y: "-13.5vh",
        //     ease: "bounceIn",
        //     scrollTrigger: {
        //         trigger: ".ai-card-container-bottom",
        //         start: "top bottom",
        //         end: "center center",
        //         scrub: 2,
        //         once: true,
        //         // markers: true,
        //     },
        // });

        // gsap.from(".security-card-container-bottom p", {
        //     duration: 1.5, // Duration of the animation in seconds
        //     opacity: 0, // Start from 0 opacity
        //     x: "-100%", // Start from left (-100% of its own width)
        //     y: "-100%", // Start from top (-100% of its own height)
        //     ease: "power3.out", // Choose an easing type
        //     scrollTrigger: {
        //         trigger: ".ai-card-container-bottom",
        //         start: "top bottom",
        //         end: "center center",
        //         scrub: 2,
        //         once: true,
        //         // markers: true,
        //     },
        // });

        // gsap.to(".image-container", {
        //     backgroundSize: "35vw 72vh",
        //     scrollTrigger: {
        //         trigger: ".image-container",
        //         start: "top bottom", // when the top of the trigger hits the center of the viewport
        //         end: "center center", // when the bottom of the trigger hits the center of the viewport
        //         scrub: 2,
        //         once: true,
        //         // markers: true,
        //     },
        // });
    },
    methods: {
        productClicked() {
            if (this.spinner_at != 1) {
                this.product_clicked = true;
                this.url_current_hassle = this.url_hassle[0];
                this.$refs.circle.style.transform = "rotate(360deg)";
                this.spinner_at = 1;
                this.maintenance_clicked = false;
                this.manage_service_clicked = false;
                this.install_clicked = false;
            }
        },
        maintenanceClicked() {
            if (this.spinner_at != 2) {
                this.maintenance_clicked = true;
                this.url_current_hassle = this.url_hassle[1];
                this.$refs.circle.style.transform = "rotate(270deg)";
                this.spinner_at = 2;
                this.product_clicked = false;
                this.manage_service_clicked = false;
                this.install_clicked = false;
            }
        },
        manageServiceClicked() {
            if (this.spinner_at != 3) {
                this.manage_service_clicked = true;
                this.$refs.circle.style.transform = "rotate(180deg)";
                this.url_current_hassle = this.url_hassle[2];
                this.spinner_at = 3;
                this.product_clicked = false;
                this.maintenance_clicked = false;
                this.install_clicked = false;
            }
        },
        installClicked() {
            if (this.spinner_at != 4) {
                this.install_clicked = true;
                this.$refs.circle.style.transform = "rotate(90deg)";
                this.url_current_hassle = this.url_hassle[3];
                this.spinner_at = 4;
                this.product_clicked = false;
                this.maintenance_clicked = false;
                this.manage_service_clicked = false;
            }
        },
        // drawLines() {
        //     const canvas = document.getElementById("linesCanvas");
        //     const ctx = canvas.getContext("2d");
        //     canvas.width = window.innerWidth * 2;
        //     canvas.height = window.innerHeight * 2;

        //     const spacing = 100;
        //     const verticalOffset = 1000; // Set the offset in pixels directly

        //     [0, 1, 2].forEach((offset) => {
        //         ctx.strokeStyle = ["#999", "#777", "#666"][offset];
        //         ctx.lineWidth = [3, 2, 1][offset];
        //         ctx.beginPath();
        //         ctx.moveTo(0 + offset * spacing, 0);
        //         ctx.lineTo(canvas.width, canvas.height - offset * spacing);
        //         ctx.stroke();
        //     });

        //     // Draw the new line 500px below the first set of lines
        //     ctx.strokeStyle = "#999"; // or any other color you prefer
        //     ctx.lineWidth = 3; // or any other width you prefer
        //     ctx.beginPath();
        //     ctx.moveTo(0, verticalOffset);
        //     ctx.lineTo(canvas.width, canvas.height + verticalOffset);
        //     ctx.stroke();

        //     [0, 1].forEach((offset) => {
        //         ctx.strokeStyle = ["#999", "#777"][offset];
        //         ctx.lineWidth = 2;
        //         ctx.beginPath();
        //         ctx.moveTo(canvas.width - offset * spacing, 0);
        //         ctx.lineTo(0, canvas.height - offset * spacing);
        //         ctx.stroke();
        //     });
        // },
    },
};
</script>

<style scoped>
/* --- RESET STYLES --- */
*,
*::before,
*::after {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* ====================== Spinner =========================== */
.container-outer-spinner {
    width: 500px;
    height: 500px;
    position: absolute;
    bottom: 250px !important;
    z-index: 10000 !important;
}
.container-spinner {
    width: 100%;
    height: 100%;
    background-color: #ccc;
    border-radius: 50%;
    position: relative;
    overflow: hidden;
    transition: 5s;
    scale: 0.55;
}
.container-spinner div {
    height: 50%;
    width: 500px;
    position: absolute;
    clip-path: polygon(100% 0, 50% 100%, 0 0);
    transform: translateX(-50%);
    transform-origin: bottom;
    text-align: center;
    display: flex;
    align-items: flex-start;
    padding: 15px;
    justify-content: center;
    font-size: 26px;
    font-weight: 700;
    font-family: sans-serif;
    color: #fff;
    left: 0px;
}

.black-layer {
    background-color: rgba(0, 0, 0, 0.5);
    width: 500px;
    height: 800px;
    background-position: bottom;
    clip-path: unset !important;
    margin-left: 200px;
    margin-top: -15px;
}

.hidden {
    display: none !important;
}

.container .product {
    background-image: url("/img/bg-options-wheel-up.png");
    background-position: bottom;
    background-size: 650px 300px;
    left: 50%;
    z-index: 10;
}

.container .maintenance {
    transform: rotate(90deg);
    background-image: url("/img/bg-options-wheel-up.png");
    background-position: bottom;
    background-size: 650px 300px;
}
.container .manage-service {
    transform: rotate(180deg);
    z-index: 100 !important;
    background-image: url("/img/bg-options-wheel-up.png");
    background-position: bottom;
    background-size: 650px 300px;
}
.container .install {
    transform: rotate(270deg);
    z-index: 0;
    background-image: url("/img/bg-options-wheel-up.png");
    background-position: bottom;
    background-size: 650px 300px;
}

#spin {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 10000 !important;
    background-color: #1d1e1e;
    text-transform: uppercase;
    font-weight: 700;
    font-size: 20px;
    color: #a2a2a2;
    width: 190px;
    height: 190px;
    font-family: sans-serif;
    border-radius: 50%;
    cursor: pointer;
    outline: none;
    letter-spacing: 1px;
    clip-path: unset !important;
}

.marker {
    width: 35px !important;
    height: 35px !important;
    background-color: #323333;
    clip-path: polygon(50% 0%, 0% 100%, 100% 100%) !important;
    position: absolute !important;
    /* top: -55px !important;
    left: 150px !important; */
    top: 0px !important;
    left: 0 !important;
    right: 0 !important;
    margin-left: auto !important;
    margin-right: auto !important;
    transform: rotate(180deg) !important;
    z-index: 5000 !important;
}

.img-marker {
    width: 120px !important;
    height: 120px !important;
    position: absolute !important;
    left: 35px !important;
    top: 40px !important;
    clip-path: unset !important;
}

.clickable {
    cursor: pointer;
}
/* ========================================================== */

.learn-more-container {
    position: relative;
    overflow: hidden;
    min-height: 100vh;
    max-height: fit-content;
    background-color: black;
    display: flex;
    flex-direction: column;
    align-content: center;
    align-items: center;
    justify-content: center;
    padding-top: 80px;
    padding-bottom: 80px;
}

#first-column {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
}

#second-column {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
}

.center-vertically {
    width: fit-content;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
    align-items: center;
}

.small-box {
    min-width: 250px;
    max-width: 300px;
    height: fit-content;
    background-color: #212121;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: flex-start;
    color: white;
    border-radius: 30px;
    scale: 0.75;
}

.medium-box-outer {
    min-width: 250px;
    max-width: 300px;
    height: 450px;
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    margin-top: 20px;
}

.medium-box {
    min-width: 250px;
    max-width: 300px;
    height: fit-content;
    padding-top: 150px;
    background-color: #212121;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: flex-start;
    color: white;
    border-radius: 30px;
    scale: 0.95;
}

.flying-img {
    position: absolute;
    top: -20px;
    left: 0;
    right: 0;
    width: 300px;
    margin-left: auto;
    margin-right: auto;
    z-index: 1000;
}

.big-box {
    min-width: 250px;
    max-width: 450px;
    min-height: 250px;
    max-height: fit-content;
    background-image: url("/img/bg-total-solution-home-page.png");
    background-size: cover;
    background-position: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: flex-start;
    color: white;
    border-radius: 40px;
}

.description-box {
    padding: 20px;
}

.outer-video {
    height: 100%;
    width: 100%;
    border-radius: 40px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
    align-items: center;
    overflow: hidden;
}

#video-section-1 {
    width: 120%;
    height: 100%;
}

.button-content-container {
    z-index: 50;
    color: white;
    margin-top: 20px;
}

.learnmore-button {
    font-size: 14px;
    text-transform: uppercase;
    letter-spacing: 2.5px;
    font-weight: 400;
    color: #f5f5f5;
    border-radius: 20px;
    transition: all 0.3s ease 0s;
    cursor: pointer;
    outline: none;
    text-align: center;
    position: relative;

    visibility: hidden;
    pointer-events: none;
}

.mt-med {
    margin-top: 100px;
}

.mt-min {
    margin-top: 50px;
}

.border-img {
    border-radius: 40px;
}

.description-box p {
    margin-top: 10px;
}

.text-bolder {
    font-weight: 600 !important;
}

h3 {
    font-weight: 400;
}

@media only screen and (max-width: 600px) {
    .big-box {
        /* margin: 15px; */
        margin: 0 auto;
    }

    .center-vertically {
        margin: 0 auto;
    }
}

@media only screen and (max-width: 960px) {
    .container-outer-spinner {
        /* bottom: 170px !important; */
        bottom: 80px !important;
    }
}
</style>
