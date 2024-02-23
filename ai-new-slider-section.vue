<template>
    <div class="new-slider-section">
        <div id="scrollContainer">
            <div id="animationContainer">
                <div class="image-container">
                    <img id="image1" src="img/home-ai/shelf.png" />

                    <img
                        id="image2"
                        src="img/home-ai/camera.png"
                        style="display: none"
                    />

                    <img
                        id="image3"
                        src="img/home-ai/green-light.png"
                        style="display: none"
                    />
                    <img
                        id="image4"
                        src="img/home-ai/shelf-small-dashboard.png"
                        style="display: none"
                    />
                </div>
                <div class="text-container">
                    <div id="text1" class="image-text">
                        <h2>{{ title_text_1 }}</h2>
                        <h3>{{ subtitle_1 }}</h3>
                        <p>{{ description_1 }}</p>
                    </div>

                    <div id="text2" class="image-text">
                        <h2>{{ title_text_2 }}</h2>
                        <h3>{{ subtitle_2 }}</h3>
                        <p>{{ description_2 }}</p>
                    </div>
                    <div id="text3" class="image-text">
                        <h2>{{ title_text_3 }}</h2>
                        <h3>{{ subtitle_3 }}</h3>
                        <p>{{ description_3 }}</p>
                    </div>
                </div>
            </div>
        </div>
        <!-- Placeholder for scrollable content to enable a large enough scrollable area -->
        <div style="height: 100vh"></div>
    </div>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { ScrollToPlugin } from "gsap/all";

gsap.registerPlugin(ScrollTrigger, ScrollToPlugin);

export default {
    props: {
        dynamicContent: {
            type: Object,
            required: true,
        },
    },
    data() {
        return {
            title_text_1: "AI Enabled",
            title_text_2: "AI Enabled",
            title_text_3: "AI Enabled",
            subtitle_1: "Shelf Monitoring",
            subtitle_2: "Shelf Monitoring",
            subtitle_3: "Shelf Monitoring",
            description_1: "Welcome to the future of retail management.",
            description_2:
                "The integration of our AI Camera enables our system to identify product types and their placement in real-time, facilitating accurate and timely replenishment monitoring.",
            description_3:
                "Our algorithm can process and summarize the data allowing real-time access on our cloud-based dashboard or for scheduled report delivery.",
            img_1: "img/home-ai/shelf.png",
            img_2: "img/home-ai/camera.png",
            img_3: "img/home-ai/green-light.png",
            // Assuming img_3 is a mistake and should be 'shelf-small-dashboard.png' based on context
            img_4: "img/home-ai/shelf-small-dashboard.png",
            ready: true, // No loading necessary for static content
            loading: false,
        };
    },

    mounted() {
        gsap.registerPlugin(ScrollTrigger);
        // Pin the animation container
        ScrollTrigger.create({
            trigger: "#animationContainer",
            start: "top center",
            scrub: true,
            pin: true,
        });

        this.animateImage1();
        this.animateImage2();
        this.animateImage3();
        this.animateImage4();

        const file = document.createElement("link");
        file.rel = "stylesheet";
        file.href = "/css/skeleton-loader.css";
        document.head.appendChild(file);

        const carousel = document.createElement("link");
        (carousel.rel = "stylesheet"),
            (carousel.href = "/css/carousel-news.css"),
            document.head.appendChild(carousel);

        this.ready = true;
        this.loading = false;
    },
    watch: {
        dynamicContent(newVal, _) {
            if (newVal.title_text_1) {
                this.title_text_1 = newVal.title_text_1;
            }

            if (newVal.title_text_2) {
                this.title_text_2 = newVal.title_text_2;
            }

            if (newVal.title_text_3) {
                this.title_text_3 = newVal.title_text_3;
            }

            if (newVal.subtitle_1) {
                this.subtitle_1 = newVal.subtitle_1;
            }

            if (newVal.subtitle_2) {
                this.subtitle_2 = newVal.subtitle_2;
            }

            if (newVal.subtitle_3) {
                this.subtitle_3 = newVal.subtitle_3;
            }

            if (newVal.image_variation_1) {
                this.img_1 = newVal.image_variation_1;
            }

            if (newVal.image_variation_2) {
                this.img_2 = newVal.image_variation_2;
            }

            if (newVal.image_variation_3) {
                this.img_3 = newVal.image_variation_3;
            }

            if (newVal.description_1) {
                this.description_1 = newVal.description_1;
            }

            if (newVal.description_2) {
                this.description_2 = newVal.description_2;
            }

            if (newVal.description_3) {
                this.description_3 = newVal.description_3;
            }
        },
    },
    methods: {
        // setupAnimation(selector, order) {
        //     gsap.from(selector, {
        //         autoAlpha: 0,
        //         x: order % 2 === 0 ? -100 : 100, // Alternate direction
        //         y: order % 2 === 0 ? -100 : 100,
        //         scrollTrigger: {
        //             trigger: "#scrollContainer",
        //             start: () => `top+=${order * 500} center`, // Calculate start point based on order
        //             end: () => `+=${500}`, // Animation length
        //             scrub: true,
        //             toggleActions: "play none none reverse",
        //             onEnter: () => gsap.set(selector, { display: "block" }),
        //             markers: true, // For debugging purposes, can be removed later
        //         },
        //     });
        // },
        animateImage1() {
            gsap.from("#image1", {
                autoAlpha: 0,
                scale: 0.5,
                scrollTrigger: {
                    trigger: "#scrollContainer",
                    start: "top center",
                    end: "top+=500 center",
                    scrub: true,
                    toggleActions: "play none none reverse",
                    onEnter: () => {
                        gsap.set("#image1", { display: "block" });
                        gsap.set("#text1", { display: "block" }); // Display the text
                    },
                    markers: true,
                },
            });
            // Text animation for Image 1
            gsap.from("#text1", {
                autoAlpha: 0,
                scrollTrigger: {
                    trigger: "#scrollContainer",
                    start: "top center",
                    end: "top+=500 center",
                    scrub: true,
                    toggleActions: "play none none reverse",
                    markers: true,
                },
            });
        },

        animateImage2() {
            gsap.from("#image2", {
                autoAlpha: 0,
                x: "-100%",
                scrollTrigger: {
                    trigger: "#scrollContainer",
                    start: "top+=500 center",
                    end: "top+=750 center",
                    scrub: true,
                    toggleActions: "play none none reverse",
                    onEnter: () => gsap.set("#image2", { display: "block" }),
                    markers: true,
                },
            });
        },

        animateImage3() {
            gsap.from("#image3", {
                autoAlpha: 0,
                scrollTrigger: {
                    trigger: "#scrollContainer",
                    start: "top+=750 center",
                    end: "top+=1000 center",
                    scrub: true,
                    toggleActions: "play none none reverse",
                    onEnter: () => gsap.set("#image3", { display: "block" }),
                    markers: true,
                },
            });
        },

        animateImage4() {
            gsap.from("#image4", {
                autoAlpha: 0,
                x: "100%",
                scrollTrigger: {
                    trigger: "#scrollContainer",
                    start: "top+=1000 center",
                    end: "top+=1500 center",
                    scrub: true,
                    toggleActions: "play none none reverse",
                    onEnter: () => gsap.set("#image4", { display: "block" }),
                    markers: true,
                },
            });
        },
    },
};
</script>

<style scoped>
.new-slider-section {
    position: relative;
    width: 100%;
}

#scrollContainer {
    position: relative;
    width: 100vw;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh; /* Ensure it's at least the height of the viewport */
}

#animationContainer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
}

.image-container,
.text-container {
    position: relative;
    width: 50%;
}

.image-container {
    position: relative;
    flex: 1;
}

.text-container {
    flex: 1;
    padding: 20px; /* Adjust as needed */
}

img,
.image-text {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    display: none; /* Start hidden, let GSAP reveal */
}
</style>
