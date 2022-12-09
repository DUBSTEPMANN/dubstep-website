<script setup>
import Button from '../components/Button.vue';
</script>

<template>
    <div class="splash-container">
        <div class="splash">
            <h1 class="splash-head">DUBSTEPMAN</h1>
            <p class="splash-subhead"> Music composer/producer/sound engineer </p>
            <Button>CONTACT ME</Button>
            <!-- TODO: Jump to contact me section on click-->
        </div>
    </div>
</template>


<style>
.splash-container {
    background: url(../assets/dubstep-pfp.png);
    background-color: black;
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
    z-index: 1;
    overflow: hidden;
    /* The following styles are required for the "scroll-over" effect */
    width: 100%;
    height: 88%;
    top: 0;
    left: 0;
    position: fixed !important;
}

.splash {
    /* absolute center .splash within .splash-container */
    width: 80%;
    height: 50%;
    margin: auto;
    position: absolute;
    top: 100px;
    left: 0;
    bottom: 0;
    right: 0;
    text-align: center;
    text-transform: uppercase;
}

/* This is the main heading that appears on the blue section */
.splash-head {
    font-size: 100px;
    font-weight: bold;
    color: white;
    font-weight: bolder;
    letter-spacing: 1cm;
    border-radius: 5px;
    line-height: 1em;
}

/* This is the subheading that appears on the blue section */
.splash-subhead {
    color: white;
    letter-spacing: 0.05em;
    opacity: 0.8;
}

@media screen and (max-width: 1200px) {
    .splash-head {
        font-size: 50px;
        letter-spacing: 0.5cm;
    }
}

@media screen and (max-width: 600px) {
    .splash-head {
        font-size: 25px;
        letter-spacing: 3px;
    }
}
</style>