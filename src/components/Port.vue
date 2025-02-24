<script setup>
import { portText } from "../constants";
</script>

<template>
    <section id="port">
            <div class="port__inner">
                <h2 class="port__title">
                    portfolio<em>포폴 작업물</em>
                </h2>
                <div class="arrow">👉</div>
                <ul class="port__wrap">
                    <li 
                        :class="`port__item p${key + 1}`" 
                        v-for="(port, key) in portText" :key="key"
                    >
                        <span class="num">{{port.num}}</span>
                        <img :src="port.img" :alt="port.name" />
                        <h3 class="title">{{port.title}}</h3>
                        <p class="desc">{{port.desc}}</p>
                        <div class="btn-box">
                            <a :href="port.code" class="code" title="code">code</a>
                            <a :href="port.view" target="_blank" class="view" title="view">view</a>
                        </div>
                    </li>
                </ul>
            </div>
        </section>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
    mounted: function(){
        this.scrollAnimation();
    },
    methods: {
        scrollAnimation(){
            const horSection = gsap.utils.toArray(".port__item");

            gsap.to(horSection, {
                xPercent: -120 * (horSection.length - 1),
                ease: "none",
                scrollTrigger: {
                    trigger: "#port",
                    start: "top 56px",
                    end: "+=3000",
                    pin: true,
                    scrub: 1,
                    markers: false,
                    invalidateOnRefresh: true,
                    anticipatePin: 1,
                },
            });
        },
    },
};
</script>

<style lang="scss" scoped>
#port {
    width: 100%;
    overflow: hidden;
}

.port__inner {
    padding: 0 16px;
}

.port__title {
    width: 100%;
    height: 10%;
    font-size: 24px;
    font-weight: 700;
    text-transform: uppercase;
    word-break: keep-all;
    border-bottom: 1px solid var(--black);
}

.port__title em {
    font-size: 18px;
    white-space: nowrap;
    margin-left: 8px;
}

.port__inner .arrow {
    font-size: 2rem;
}

.port__wrap {
    display: flex;
    flex-wrap: wrap;
    width: 7000px;
}

.port__wrap .port__item {
    width: 500px;
    padding: 2.5rem;
    margin-right: 20px;
}

.port__wrap .port__item.p1 {
    background-color: var(--subBg100);
}

.port__wrap .port__item.p2 {
    background-color: var(--subBg200);
}

.port__wrap .port__item.p3 {
    background-color: var(--subBg300);
}

.port__wrap .port__item.p4 {
    background-color: var(--subBg400);
}

.port__wrap .port__item.p5 {
    background-color: var(--subBg500);
}

.port__wrap .port__item .num {
    font-size: 2rem;
    font-weight: 700;
}

.port__wrap .port__item .title {
    font-size: 1.5rem;
    padding: 1rem 0;
    font-weight: 700;
    color: var(--black);
    border-bottom: 1px solid #414141;
    margin-bottom: 1rem;
}

.port__wrap .port__item .desc {
    font-size: 1rem;
}

.port__wrap .port__item .btn-box {
    margin-top: 2rem;
    display: flex;
    gap: 10px;
}

.port__wrap .port__item .btn-box a {
    font-size: 1rem;
    border-radius: 4px;
    color: var(--white);
    padding: 0.6rem 1rem;
    transition: 0.3s;
    align-items: center;
    justify-content: center;
    text-align: center;
}

.port__wrap .port__item .btn-box .code {
    color: #3e3e3e;
    border: 1px solid #b09c90;
}

.port__wrap .port__item .btn-box .code:hover {
    color: #353535;
    border: 1px solid #969696;
    font-weight: bold;
}

.port__wrap .port__item .btn-box .code::after {
    content: attr(title);
    display: block;
    font-weight: bold;
    height: 0px;
    transform: translateY(-18px);
    visibility: hidden;
}

.port__wrap .port__item .btn-box .view {
    background-color: rgb(54, 54, 53);
    border: 1px solid transparent;
}

.port__wrap .port__item .btn-box .view:hover {
    font-weight: bold;
    background-color: #121212;
}

.port__wrap .port__item .btn-box .view::after {
    content: attr(title);
    display: block;
    font-weight: bold;
    height: 0px;
    transform: translateY(-18px);
    visibility: hidden;
}

@media (max-width: 800px) {
    .port__wrap .port__item {
        width: 400px;
    }
}
</style>