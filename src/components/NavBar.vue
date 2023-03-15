<script setup>
    import { RouterLink } from 'vue-router';
</script>

<template>
    <nav id="">
        <img id="LargeLogo" src="https://willydean.com/assets/images/Logo.png" height="50" width="200" alt="Logo">
        <img id="SmallLogo" src="https://willydean.com/assets/images/LogoSmall.png" height="50" width="80" alt="Logo">
        <button @click="HideNav" id="HideNav">Hide/Show</button>
        <RouterLink id="" class="bold" to="/">Home</RouterLink>
        <RouterLink id="" to="/about">Projects</RouterLink>
        <RouterLink id="" to="/about">What's new</RouterLink>
        <RouterLink id="" to="/about">Test</RouterLink>
        <RouterLink id="" to="/about">Link</RouterLink>
        <RouterLink id="" to="/about">About Me</RouterLink>
    </nav>
</template>

<script>

</script>

<style scoped>

/* large/landscape screens */
@media (width >= 1000px){
    #SmallLogo {
        display:none;
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
}
/* Small/portrait screens */
@media (width < 1000px){
    #LargeLogo {
        display: none;
    }
    nav {
    animation-name: HideBar;
    animation-duration: 2s;
    position: fixed;
    top: 0;
    left: 0;
    display: flex;
    justify-content: left;
    align-items: left;
    flex-direction:column;
    width: 10rem;
    height: 100%;
    background-color: #161616;
    z-index: 2;
    animation-fill-mode: forwards;
    }
    a {
        padding-top: 2rem;
        animation-name: Hide;
        animation-duration: 2s;
    }
    img {
        margin-top: 1rem; 
        margin-left: 0.5rem; 
    }
    button{
        margin-right: auto;
        padding-right: 2rem;
    }
    nav#HideNav{
        animation-name: HideBar;
        animation-duration: 2s;
    }
    nav#ShowNav{
        animation-name: ShowBar;
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

a#HideNav{
    animation-name: Hide;
    animation-duration: 2s;
}

a#ShowNav{
    animation-name: Show;
    animation-duration: 2s;
}




@keyframes Hide {
    from {}
    to { opacity: 0; }
}

@keyframes Show {
    from { opacity: 0;}
    100% { opacity: 1;}
}

@keyframes HideBar {
    from {}
    to { height: 10%; }
}

@keyframes ShowBar {
    from { height: 10% }
    to { height: 100%;}
}


</style>

<script>
export default {
    methods: {
        HideNav(){
            if (this.$el.id == "ShowNav" || this.$el.id == "") {
                this.$el.id = "HideNav";
            } else {
                this.$el.id = "ShowNav";
            }
            for(let i = 0; i < this.$el.children.length; i++){
                let idName = this.$el.children[i].id;
                if (idName == "ShowNav" || idName == ""){
                    this.$el.children[i].id = "HideNav";
                } else if (idName == "HideNav") {
                    this.$el.children[i].id = "ShowNav";
                }
            }
        }
    }
}
</script>