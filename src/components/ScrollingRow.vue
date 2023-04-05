<script setup>
    import { def } from '@vue/shared';
import { RouterLink } from 'vue-router';
</script>

<template>
    <section>
        <h1>{{ displayText }}</h1>
        <div class="container">
            <button @click="ScrollLeft" class="scrollLeft"><img src='https://willydean.com/assets/images/ArrowLeft.png' placeholder="Arrow"></button>
            <button @click="ScrollRight" class="scrollRight"><img src='https://willydean.com/assets/images/ArrowRight.png' placeholder="Arrow"></button>
            <div class="scrollRow">
                <component :is="link.blank ? 'span' : 'a'" v-for="link in localLinks" :href="link.url" target="_blank"><img id="poster" :src="link.image" alt=""></component>
            </div>
            
        </div>
    </section>
</template>

<script>

export default {
    props: {
        displayText: String,
        placeHolder: Boolean,
        links: Array,
    },
    data(){
        return {
            rowPointer: {},
            localLinks: [],
            randomImage: [],
            images: [
                'https://willydean.com/assets/images/PH1.jpg',
                'https://willydean.com/assets/images/PH2.jpg',
                'https://willydean.com/assets/images/PH3.jpg',
                'https://willydean.com/assets/images/PH4.jpg',
                'https://willydean.com/assets/images/PH5.jpg',
                'https://willydean.com/assets/images/PH6.jpg',
                'https://willydean.com/assets/images/PH7.jpg',
                'https://willydean.com/assets/images/PH8.jpg',
                'https://willydean.com/assets/images/PH9.jpg',
                'https://willydean.com/assets/images/PH10.jpg',
                'https://willydean.com/assets/images/PH11.jpg',
                'https://willydean.com/assets/images/PH12.jpg',
                'https://willydean.com/assets/images/PH13.jpg',
                'https://willydean.com/assets/images/PH14.jpg',
                'https://willydean.com/assets/images/PH15.jpg',
                'https://willydean.com/assets/images/PH16.jpg',
                'https://willydean.com/assets/images/PH17.jpg',
                'https://willydean.com/assets/images/PH18.jpg',
                'https://willydean.com/assets/images/PH19.jpg',
                'https://willydean.com/assets/images/PH20.jpg',
            ]
        }
    },
    methods: {
        ScrollLeft() {
            this.$el.children[1].children[2].scrollLeft -= window.innerWidth*0.12;
        },
        ScrollRight(){
            this.$el.children[1].children[2].scrollLeft += window.innerWidth*0.12;
        }
    },
    created(){
        let tempBool = this.placeHolder;
        if (tempBool) {
            this.images.forEach((image, index) => {
                this.localLinks.push({
                    title: "blank",
                    url: '/',
                    image: this.images[Math.floor(Math.random()*this.images.length)],
                    blank: true,
                });
                
            });
        } else if (!tempBool) {
            this.localLinks.push(...this.links);
        }
    }
}
</script>

<style scoped>
section {
    padding-left: 4rem;
    padding-top: 1rem;
}

h1 {
    font-size: 2vmin;
    display: block;
    color: #ddd;
    margin: 0.5rem;
    margin-left: 0;
}
img{
    padding: 0 0.2rem 0 0.2rem;
    scroll-snap-align: start;
    height: 12vw;
    width: auto;
    transition: all .2s ease-in-out;
    transition-delay: 0.5s;
}

#poster:hover{
    transform: scale(1.75);
}

.container{
    padding: 100px 0;
    margin: -100px 0;
}

/* container for the image carousel */
.scrollRow{
    display: flex;
    overflow-x: hidden;
    scroll-snap-type: x mandatory;
    padding: 100px 0;
    margin: -100px 0;
    
}

.scrollRow::-webkit-scrollbar {
    display: auto;
}

button{
    font-weight:normal;
    font-size: xx-large;
    color: #686868;
    background-color: transparent;
    border-radius: 50%;
    border: none;
    height: 12vw;
    width: 8vw;
    z-index: 1;
}
/* remove scroll buttons for touch devices */
@media (hover: none) and (pointer: coarse) {
    button{
        display: none;
    }
}
.scrollLeft{
    position: absolute;
    opacity: 0.4;
}
.scrollRight{
    position: absolute;
    right: 1rem;
    opacity: 0.4;
}

/* if small screen or portrait */
@media (width < 1000px) or (orientation: portrait){
    section {
        padding-left: 1rem;
        padding-top: 1rem;  
    }
}

</style>