<script setup>
import { siteText } from "../constants";
</script>

<template>
    <section id="site">
            <div class="site__inner">
                <h2 class="site__title">Site coding <em>나의 작업물</em></h2>
                <div class="site__wrap">
                    <article
                        :class="`site__item s${key + 1}`"
                        v-for="(site, key) in siteText" :key="key"
                    >
                        <span class="num">{{key+1}}.</span>
                        <div class="text">
                            <p v-for="(text, index) in site.text" :key="index">{{ text }}</p>
                        </div>
                        <h3 class="title">{{site.title}}</h3>
                        <div class="btn-box">
                            <a :href="site.code" title="code">code</a>
                            <a :href="site.view" title="view">view</a>
                        </div>
                        <div class="info" >
                            <span v-for="(info, index) in site.info" :key="index">{{info}}</span>
                        </div>
                    </article>
                </div>
            </div>
        </section>
</template>

<style lang="scss" scoped>
.site__inner {
    margin: 10vh 0;
    padding: 0 16px;
}

.site__title {
    width: 100%;
    height: 10%;
    font-size: 24px;
    font-weight: 700;
    text-transform: uppercase;
    word-break: keep-all;
    border-bottom: 1px solid var(--black);
    background-color: var(--mainBg-color);
    position: sticky;
    top: 70px;
    left: 0;
    margin-bottom: 30px;
}

.site__title em {
    font-size: 18px;
    white-space: nowrap;
    margin-left: 8px;
}

.site__item {
    height: 70vh;
    padding: 1rem;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    position: sticky;
    left: 0;
}

.site__item.s1 {
    background-color: rgb(235, 234, 233);
    top: 120px;
}

.site__item.s2 {
    background-color: rgb(228, 226, 223);
    top: 200px;
}

.site__item.s3 {
    background-color: rgb(214, 211, 208);
    top: 280px;
}

.site__item.s4 {
    background-color: rgb(195, 193, 192);
}

.site__item .num {
    font-size: 5vw;
    line-height: 1;
    font-weight: 800;
    position: absolute;
    left: 3vw;
    top: 3vw;
}

.site__item .text {
    text-align: center;
}

.site__item .text > p {
    font-size: 5vw;
    line-height: 1.2;
    font-weight: 900;
    text-transform: uppercase;
}

.site__item .title {
    margin-top: 1.2rem;
    font-size: 1.2rem;
}

.site__item .btn-box {
    margin-top: 2rem;
    display: flex;
    gap: 10px;
}

.site__item .btn-box a {
    font-size: 1rem;
    border-radius: 4px;
    color: var(--white);
    padding: 0.6rem 1rem;
    transition: 0.3s;
    align-items: center;
    justify-content: center;
    text-align: center;
}

.site__item .btn-box a:nth-child(1) {
    color: #3e3e3e;
    border: 1px solid #bbbaba;
}

.site__item .btn-box a:nth-child(1):hover {
    color: #353535;
    font-weight: bold;
    border: 1px solid #969696;
}

.site__item .btn-box a:nth-child(1)::after {
    content: attr(title);
    display: block;
    font-weight: bold;
    height: 0px;
    transform: translateY(-18px);
    visibility: hidden;
}

.site__item .btn-box a:nth-child(2) {
    background-color: rgb(54, 54, 53);
    border: 1px solid transparent;
}

.site__item .btn-box a:nth-child(2):hover {
    font-weight: bold;
    background-color: #121212;
}

.site__item .btn-box a:nth-child(2)::after {
    content: attr(title);
    display: block;
    font-weight: bold;
    height: 0px;
    transform: translateY(-18px);
    visibility: hidden;
}

.site__item .info {
    position: absolute;
    left: 50%;
    bottom: 0;
    transform: translate(-50%, 0);
    margin-bottom: 20px;
    width: 95%;
    border-top: 1px solid #969696;
    border-bottom: 1px solid #969696;
    display: flex;
    justify-content: space-between;
    padding: 8px 0;
}

.site__item .info p {
    font-size: 0.8rem;
    text-transform: uppercase;
}

@media (max-width: 800px) {
    .site__item .text > p {
        font-size: 8vw;
    }

    .site__item .info {
        flex-direction: column;
        padding: 5px 0;
    }
}
</style>