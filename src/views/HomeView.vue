<script setup>
    import Skip from "@/components/Skip.vue"
    import AppHeader from "@/components/AppHeader.vue"
    import Intro from "@/components/Intro.vue"
    import Skill from "@/components/Skill.vue"
    import Site from "@/components/Site.vue"
    import Port from "@/components/Port.vue"
    import Contact from "@/components/Contact.vue"
    import AppFooter from "@/components/AppFooter.vue"
 </script>

<template>
    <Skip />
    <AppHeader />
    <main id="main" role="main">
        <Intro />
        <Skill />
        <Site />
        <Port />
        <Contact />
    </main>
    <AppFooter />
</template>
