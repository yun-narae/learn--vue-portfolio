<script setup>
import { footerText } from "../constants";
</script>

<template>
    <footer id="footer">
        <div class="footer__inner">
            <h2 class="footer__text">
                <div>webstoryboy</div>
                <div>@webs</div>
            </h2>
            <div class="footer__info">
                <div class="left">
                    <div class="title">
                        <a href="#">sign up</a>
                    </div>
                    <p>회원가입을 하시면 댓글과 게시판 기능을 이용할 수 있습니다.</p>
                </div>
                <div class="right">
                    <h3>social</h3>
                    <ul>
                        <li v-for="(footer, key) in footerText" :key="key">
                            <a :href="footer.link">{{ footer.title }}</a>
                            <em>{{ footer.desc }}</em>
                        </li>
                    </ul>
                </div>
            </div>
            <div class="footer__right">
                © 2023 webstoryboy<br />
                이 사이트는 비트를 이용하여 제작하였습니다.
            </div>
        </div>
    </footer>
</template>

<style lang="scss" scoped>
    #footer {
    font-family: var(--mainKor-font);
}

.footer__inner {
    padding: 16px;
}

.footer__text {
    font-size: 12px;
    text-transform: uppercase;
    border-top: 1px solid var(--black);
    border-bottom: 1px solid var(--black);
    display: flex;
    justify-content: space-between;
}

.footer__info {
    display: flex;
    justify-content: space-between;
    margin: 100px 0;
}

.footer__info .left {
    width: 40%;
}

.footer__info .left .title {
    border-top: 2px solid var(--black);
    border-bottom: 1px solid var(--black);
    padding: 20px 0;
    text-transform: uppercase;
    font-weight: 700;
    background: url("@/assets/img/arrow.svg") no-repeat right 20px;
    transition: all 0.3s;
}

.footer__info .left .title:hover {
    padding-left: 10px;
}

.footer__info .left .desc {
    font-size: 12px;
    padding-top: 20px;
}

.footer__info .right {
    width: 50%;
}

.footer__info .right h3 {
    border-top: 2px solid var(--black);
    font-size: 10px;
    margin-bottom: 40px;
    padding-top: 10px;
}

.footer__info .right ul {
    border-top: 1px solid var(--black);
}

.footer__info .right li {
    border-bottom: 1px solid var(--black);
}

.footer__info .right li a {
    padding: 14px 0;
    font-size: 14px;
    display: inline-block;
    text-transform: uppercase;
}

.footer__info .right li em {
    font-size: 12px;
    padding-left: 10px;
    opacity: 0;
    transition: all 0.3s;
}

.footer__info .right li:hover em {
    opacity: 1;
}

.footer__right {
    text-align: center;
    text-transform: uppercase;
    font-size: 12px;
    margin-bottom: 20px;
}

@media (max-width: 800px){
    .footer__info {
        flex-direction: column;
    }

    .footer__info .left {
        width: 100%;
    }

    .footer__info .left .desc {
        margin-bottom: 40px;
    }

    .footer__info .right {
        width: 100%;
    }
}
</style>