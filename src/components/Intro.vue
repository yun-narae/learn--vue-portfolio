<script setup>
import { introText } from "../constants";
</script>

<template>
    <section id="intro">
            <div class="intro__inner">
                <h1 class="intro__title">{{ introText.title }}<br/><span>scroll down ⬇️</span></h1>
                <div class="intro__text">
                    <div class="text">
                        <div  v-for="(text, key) in introText.desc" :key="key">
                            {{ text }}
                        </div>
                    </div>
                    <div className="img">
                        <img src="@/assets/img/aboutme.jpg" alt="어바웃미" />
                    </div>
                </div>
            </div>
        </section>
</template>

<style lang="scss" scoped>
#intro {
    height: 100vh;

}

.intro__inner {
    width: 100%;
    height: 100vh;
    overflow: hidden;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    flex-direction: column;
    padding: 16px;

    .intro__title {
        // width: 100%;
        font-size: 10vw;
        text-transform: uppercase;
        line-height: 1;
        font-weight: 800;
        white-space: nowrap;
        text-indent: -0.5vw;
        letter-spacing: -0.3vw;
        position: absolute;
        bottom: 30px;
        
        span {
            font-size: 14px;
            letter-spacing: 0;
            margin-top: 12px;
            color: var(--white);
            position: absolute;
            left: 60%;
            bottom: -24px;
            width:auto;
            transform:translate(-50%,-50%);
        }
    }
    .intro__text {
        display: flex;
        align-items: center;
        justify-content: left;
        
        .text {
            font-size: 3vw;
            line-height: 1;
            font-weight: 900;
            text-transform: uppercase;
            position: relative;
            transition: all 0.3s;
            cursor: all-scroll;
            margin-bottom: 140px;

            >:nth-child(1) {
                text-indent: -0.5vw;
            }

            @media (max-width: 800px){ 
                font-size: 24px;
            }
        }

        .img {
            position: absolute;
            z-index: -1;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            width: 100%;
            height: 100%;
            overflow: hidden;
            filter: grayscale(100%);
            transition: all 0.3s;
            display: flex;
            justify-content: center;
            align-items: center;

            img {
                width: 100%;
                height: 120%;
                object-fit: cover; /* 이미지를 잘라내면서 화면을 꽉 채움 */
                object-position: bottom; /* 이미지를 정가운데에 위치시킴 */
                @media (max-width: 800px){ 
                    height: 160%;
                    object-position: center -100px;
                }
            }
        }

        &:hover .text {
            opacity: 0;
        }
        &:hover .img {
            filter: grayscale(0);
        }
    }
}
</style>