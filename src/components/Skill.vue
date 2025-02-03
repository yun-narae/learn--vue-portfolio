<script setup>
import { skillText } from "../constants";
</script>

<template>
    <section id="skill">
        <div class="skill__inner">
            <h2 class="skill__title">Challenge <em>나의 도전</em></h2>
            <div class="skill__desc">
                <div v-for="(skill, key) in skillText" :key="key">
                    <h3><span>{{key+1}}.</span>{{skill.title}}</h3>
                    <p>{{skill.desc}}</p>
                </div>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
    .skill__inner {
    padding: 16px;
    display: flex;
    justify-content: space-between;

    @media (max-width: 800px){ 
        flex-direction: column;
    }

    .skill__title {
        position: sticky;
        top: 70px;
        left: 0;
        width: 48%;
        height: 5vw;
        font-size: 4vw;
        font-weight: 900;
        line-height: 1.6;
        font-family: var(--mainKor-font);
        text-transform: uppercase;
        color: var(--black100);
        border-bottom: 4px solid var(--black100);
        display: flex;
        white-space: nowrap;
        
        
        @media (max-width: 800px){ 
            width: 100%;
            margin-bottom: 10vw;
            font-size: 30px;
            height: auto;
            top: 68px;
            background-color: var(--mainBg-color);
        }
        
        em {
            align-self: self-end;
            display: block;
            font-size: 1.25rem;
            font-weight: 400;
            line-height: 2;
            margin-left: 12px;
        }
    }
    .skill__desc {
        width: 50%;

        @media (max-width: 800px){ 
            width: 100%;
        }

        h3 {
            font-size: 2vw;
            margin-bottom: 1vw;
            font-weight: 800;
            @media (max-width: 800px){ 
                font-size: 5vw;
            }
        }
        
        span {
            display: inline-block;
            transform: translateY(4px);
            margin-right: 12px;
            font-size: 4vw;
            line-height: 1;
            font-weight: 900;
            line-height: 1.3;
            font-family: var(--mainNum-font);

            @media (max-width: 800px){ 
                font-size: 15vw;
            }
        }

        p {
            margin-bottom: 30vh;
            font-size: 1.1rem;
            line-height: 1.5;
            font-weight: 500;
        }
    }
}
</style>