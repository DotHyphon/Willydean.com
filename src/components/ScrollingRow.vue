<script setup>
    import { def } from '@vue/shared';
import { RouterLink } from 'vue-router';
</script>

<template>
    <section>
        <h1>{{ displayText }}</h1>
        <div class="container">
            <!-- <button @click="ScrollLeft" class="scrollLeft"><img src='https://willydean.com/assets/images/ArrowLeft.png' placeholder="Arrow"></button> -->
            <!-- <button @click="ScrollRight" class="scrollRight"><img src='https://willydean.com/assets/images/ArrowRight.png' placeholder="Arrow"></button> -->
            <div class="scrollRow" @mousedown="StartScroll" @mouseup="EndScroll" @touchstart="StartScroll" @touchend="EndScroll">
                <component :is="link.blank ? 'span' : 'a'" v-for="link in localLinks" :href="link.url" target="_blank" @click.prevent="" @mousedown="CheckClick" @mouseup="CheckLink" @touchstart="CheckClick" @touchend="CheckLink"><img id="poster" :src="link.image" alt=""></component>
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
            tempLink: null,
            checkScroll: false,
            scroll: false,
            scrollPositionX: 0,
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
        StartScroll(e) {
            this.checkScroll = true;
            if (e.type == "touchstart") {
                this.scrollPositionX = e.touches[0].clientX;
            } else {
                e.preventDefault();
                this.scrollPositionX = e.clientX;
            }
        },
        Scroll(e) {
            
            if (this.checkScroll && !this.scroll) {
                if (e.type == "touchmove") {
                    if (Math.abs(this.scrollPositionX - e.touches[0].clientX) > 20) {
                        this.scrollPositionX = e.touches[0].clientX
                        this.checkScroll = false;
                        this.scroll = true;    
                        this.tempLink = null;                
                    }
                } else {
                    e.preventDefault();
                    if (Math.abs(this.scrollPositionX - e.clientX) > 20) {
                        this.scrollPositionX = e.clientX
                        this.checkScroll = false;
                        this.scroll = true;   
                        this.tempLink = null;                 
                    }
                }
            } else if(this.scroll) {
                let scrollX = 0;
                if (e.type == "touchmove" ) {
                    scrollX = this.scrollPositionX - e.touches[0].clientX;
                    this.scrollPositionX = e.touches[0].clientX;
                } else {
                    e.preventDefault();
                    scrollX = this.scrollPositionX - e.clientX;
                    this.scrollPositionX = e.clientX;
                }
                this.$el.children[1].children[0].scrollLeft += scrollX;
            }
        },
        EndScroll(e) {
            e.preventDefault();
            this.checkScroll = false;
            this.scroll = false;

        },
        CheckClick(e) {
            e.preventDefault();
            if (e.which == 1 || e.type == "touchstart") {
                this.tempLink = e.currentTarget.href;
            }
        },
        CheckLink(e) {
            e.preventDefault();
            if (this.tempLink) {
               window.open(this.tempLink, '_blank');
            }
        },
    },
    created(){
        document.body.addEventListener('mouseup', this.EndScroll);
        document.body.addEventListener('touchend', this.EndScroll);
        document.body.addEventListener('mousemove', this.Scroll);
        document.body.addEventListener('touchmove', this.Scroll);
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
    padding-top: 0.5rem;
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
    /* scroll-snap-align: start; */
    height: 12vw;
    width: auto;
    transition: all .2s ease-in-out;
    transition-delay: 0.5s;
}

#poster:hover:not(:active){
    transform: scale(1.75);
}


/* container for the image carousel */
.scrollRow{
    display: flex;
    overflow-x: hidden;
    /* scroll-snap-type: x mandatory; */
    padding: 10vw 0;
    margin: -10vw 0;
    
}

.scrollRow::-webkit-scrollbar {
    display: auto;
}

/* if small screen or portrait */
@media (width < 1000px) or (orientation: portrait){
    section {
        padding-left: 1rem;
        padding-top: 0.5rem;  
    }
}

</style>