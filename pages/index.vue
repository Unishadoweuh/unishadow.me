<template>
    <x-flex>
        <x-flex-section>
            <article class="intro-wrapper">
                <SectionIntro></SectionIntro>
            </article>
        </x-flex-section>

        <!---------------------------------------------------------------------------------------------------->

        <x-flex-section>
            <section class="content">
                <div v-if="options.sections.projects">
                    <h1>Projets</h1>

                    <article class="projects-wrapper">
                        <SectionProjects></SectionProjects>
                    </article>
                </div>

                <!-------------------------------------------------------------------------------------------->

                <div v-if="options.sections.experience">
                    <h1>Expériences</h1>

                    <article class="career-wrapper">
                        <SectionExperience></SectionExperience>
                    </article>
                </div>

                <!-------------------------------------------------------------------------------------------->

                <div v-if="options.sections.skills">
                    <h1>Compétences</h1>

                    <article class="skills-wrapper">
                        <SectionSkills></SectionSkills>
                    </article>
                </div>
            </section>

            <!------------------------------------------------------------------------------------------------>

            <Footer></Footer>
        </x-flex-section>
    </x-flex>
</template>

<script>
import * as options from "~~/data/options.json";
export default {
    data() {
        return {
            options
        };
    }
}
</script>

<style lang="scss" scoped>
@import "@/assets/core.scss";

article {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    flex-shrink: 1;

    &.projects-wrapper,
    &.career-wrapper,
    &.skills-wrapper {
        margin-bottom: 100px;
    }
}

x-flex {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    height: 100vh;

    x-flex-section {
        flex-grow: 1;
        flex-shrink: 1;
        flex-basis: 50%;
        display: flex;
        flex-direction: column;
        align-items: center;
        overflow-y: scroll;

        &:first-of-type {
            flex-basis: 30%;
            max-width: 500px;
        }

        &:last-of-type {
            padding: 0 50px;
            padding-top: 50px;
            margin: 0 auto;
            max-height: 100%;
            overflow-y: scroll;
        }
    }

    section.content {
        max-width: 960px;
        margin: 0 auto;
    }
}

h1 {
    text-align: center;
    margin: 20px 0;
}

//
// Mobile layouts
//
@media (max-width: $mobile) {
    x-flex {
        flex-direction: column;
        height: unset;

        x-flex-section {
            flex-basis: 100% !important;
            width: 100%;
            overflow-y: scroll;
            height: unset;
            max-height: unset !important;
            max-width: unset !important;

            &:last-of-type {
                padding-left: 20px;
                padding-right: 20px;
            }
        }
    }

    .intro-wrapper {
        width: 100%;
    }
}
</style>