<script setup>
    import { RouterLink } from 'vue-router';
</script>

<template>
    <main>
        <img id="LargeLogoTop" src="https://willydean.com/assets/images/Logo.png" height="50" width="200" alt="Logo">
        <nav id="Blank">
            <img id="LargeLogo" src="https://willydean.com/assets/images/Logo.png" height="50" width="200" alt="Logo">
            <img id="SmallLogo" src="https://willydean.com/assets/images/LogoSmall.png" height="50" width="80" alt="Logo">
            <button @click="HideNav" id="NavSlider">></button>
            <RouterLink id="Blank" class="bold" to="/">Home</RouterLink>
            <!-- <RouterLink id="Blank" to="/about">Projects</RouterLink>
            <RouterLink id="Blank" to="/about">What's new</RouterLink>
            <RouterLink id="Blank" to="/about">Test</RouterLink>
            <RouterLink id="Blank" to="/about">Link</RouterLink>
            <RouterLink id="Blank" to="/about">About Me</RouterLink> -->
        </nav>
    </main>
</template>

<script>

</script>

<style scoped>

/* large/landscape screens */
@media (width >= 0px){
    #SmallLogo {
        display:none;
    }
    #LargeLogoTop{
        display: none;
    }
    nav {
    position: fixed;
    top: 0;
    left: 0;
    display: flex;
    justify-content: left;
    align-items: center;
    flex-direction:row;
    width: 100%;
    height: 10%;
    background-color: #161616;
    z-index: 2;
    }
    img {
        margin-left: 4.7rem; 
    }
    #NavSlider{
        display: none;
    }
}

/* Small/portrait screens */
@media (width < 0px) and (orientation: portrait){
    #LargeLogo {
        display: none;
    }
    #LargeLogoTop{
        position: absolute;
        left: 50%;
        margin-left: -100px;
    }
    nav {
    position: fixed;
    top: 0;
    left: 0;
    display: flex;
    justify-content: left;
    align-items: left;
    flex-direction:column;
    width: 0;
    height: 120%;
    background-color: #161616;
    z-index: 2;
    animation-fill-mode: forwards;
    }
    a {
        padding-top: 2rem;
        visibility: hidden;
        white-space: nowrap;
    }
    img {
        align-self: center;
        padding-right: 3rem;
        padding-top: 2rem;
    }
    nav#HideNav{
        animation-name: HideBar;
        animation-duration: 2s;
    }
    nav#ShowNav{
        animation-name: ShowBar;
        animation-duration: 2s;
    }
    a#HideNav{
        animation-name: Hide;
        animation-duration: 2s;
    }
    a#ShowNav{
        animation-name: Show;
        animation-duration: 2s;
    }
} 


a {
    color: #686868;
    padding-right: 2rem;
    padding-left: 0.4rem;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: normal;
    font-size: large;
    text-decoration: none;
    animation-fill-mode: forwards;
}
button {
    color: #686868;
    background-color: transparent;
    border: none;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: normal;
    font-size: large;
    text-decoration: none;
}

.bold{
    font-weight: bold;
    color: #dddd;
}


/* Animations */
@keyframes Hide {
    from { opacity: 1; visibility: visible;}
    30% {opacity: 0;}
    to { opacity: 0; visibility: hidden; }
}

@keyframes Show {
    from { opacity: 0; visibility: hidden;}
    20% {opacity: 0;}
    to { opacity: 1; visibility: visible;}
}

@keyframes HideBar {
    from {width: 10rem; }
    to { width: 0; }
}

@keyframes ShowBar {
    from { width: 0 }
    to { width: 10rem;}
}


</style>

<script>
export default {
    methods: {
        HideNav(){
            this.$el.children[1];
            if (this.$el.children[1].id == "HideNav" || this.$el.children[1].id == "Blank") {
                this.$el.children[1].id = "ShowNav";
            } else {
                this.$el.children[1].id = "HideNav";
            }
            for(let i = 0; i < this.$el.children[1].children.length; i++){
                let idName = this.$el.children[1].children[i].id;
                if (idName == "HideNav" || idName == "Blank"){
                    this.$el.children[1].children[i].id = "ShowNav";
                } else if (idName == "ShowNav") {
                    this.$el.children[1].children[i].id = "HideNav";
                }
            }
        }
    }
}
</script>