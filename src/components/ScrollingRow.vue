<script setup>
    import { def } from '@vue/shared';
import { RouterLink } from 'vue-router';
</script>

<template>
    <section>
        <h1>{{ displayText }}</h1>
        <div class="container">
            <button @click="ScrollLeft" class="scrollLeft">&lt</button>
            <button @click="ScrollRight" class="scrollRight">></button>
            <div class="scrollRow">
                <img v-for="image in randomImage" :src="image" alt="">

            </div>
            
        </div>
    </section>
</template>

<script>

export default {
    props: {
        displayText: String,
    },
    data(){
        return {
            rowPointer: {},
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
            this.$el.children[1].children[2].scrollLeft -= 200;
        },
        ScrollRight(){
            this.$el.children[1].children[2].scrollLeft += 200;
        }
    },
    created(){
        this.images.forEach((image, index) => this.randomImage.push(this.images[Math.floor(Math.random()*this.images.length)]));
    }
}
</script>

<style scoped>
section {
    padding-left: 4rem;
    padding-top: 1rem;
}

h1 {
    display: block;
    color: #ddd;
    margin: 0.5rem;
    margin-left: 0;
}
img{
    padding: 0 0.2rem 0 0.2rem;
    scroll-snap-align: start;
    max-width: 300px;

}
.container {
    display: inline;
    white-space: nowrap;
}

.scrollRow{
    display: flex;
    overflow-x:scroll;
    scroll-snap-type: x mandatory;
    overflow-x: hidden;
}

button{
    font-weight: bold;
    font-size: xx-large;
    color: #686868;
    background-color: #161616;
    border-radius: 50%;
    border: none;
}
.scrollLeft{
    position: absolute;
    margin-top: 5rem;
}
.scrollRight{
    position: absolute;
    margin-top: 5rem;
    right: 1rem;
}

</style>