<template>
    <div class="intro">
        <div class="intro-inner">
            <div class="avatar" :style="`background-image: url('${options.avatar}')`"></div>
            <h1>{{ options.name }}</h1>

            <SocialLinks></SocialLinks>
            
            <p v-html="intro"></p>
        </div>
    </div>
</template>

<script>
import * as career from '~~/data/experience.json';
import * as options from "~~/data/options.json";

export default {
    data() {
        return {
            career,
            options
        };
    },
    computed: {
        currentJobCompany() {
            return career[career.length - 1].company;
        },
        currentJobTitle() {
            return career[career.length - 1].title;
        },
        intro() {
            return options.intro.replaceAll("\n", "<br>")
        }
    }
}
</script>

<style lang="scss" scoped>
@import "@/assets/core.scss";

.intro {
    height: 100vh;
    width: 100%;

    overflow: hidden;
    padding: 0 50px;
    position: relative;

    // We want to use glass with no distance and no hover, so we need to
    // use the internal function here..
    @include glass-internal(0px);

    .avatar {
        width: 200px;
        height: 200px;
        border-radius: 50%;
        background-size: cover;
        background-position: center;
    }

    .intro-inner {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: center;

        height: 100%;
        width: 100%;
        gap: 20px;
    }
}

//
// Mobile layouts
//
@media (max-width: $mobile) {
    .intro {
        padding: 0 20px;
        overflow: unset;

        height: 75vh;
        
        border-top: 0;
        border-left: 0;
        border-right: 0;

        .intro-inner {
            align-items: center;
            justify-content: center;
            text-align: center;
        }
    }
}

//
// Desktop layouts
//
@media (min-width: $mobile) {
    .intro {
        border-top: 0;
        border-left: 0;
        border-bottom: 0;
    }
}

//
// Anims
//
@keyframes blink {
    0% {
        opacity: 1;
    }

    50% {
        opacity: 0;
    }

    100% {
        opacity: 1;
    }
}
</style>