<script setup>
import { headerNav } from "../constants";
</script>

<template>
    <header id="header">
        <div class="hader__inner">
            <div class="header__logo" tabindex="1">
                <h1>
                    <a href="#">portfolio<em>vite</em></a>
                </h1>
            </div>
            <nav 
                class="header__nav"
                :class="{show: isNavVisible}"
                id="headerNav"
            >
            <!-- :class="['header__nav', {show: isNavVisible}]" -->
                <ul>
                    <li v-for="(nav, key) in headerNav" :key="key">
                        <a :href="nav.url" @click="scrollLink($event)">{{ nav.title }}</a>
                    </li>
                </ul>
            </nav>
            <button
                class="header__nav__mobile"
                id="headerToggle"
                aria-controls="headerNav"
                :aria-expanded="isNavVisible.toString()"
                @click="toggleMobileMenu"
            >
                <span></span>
            </button>
        </div>
    </header>
</template>

<script>
export default {
    data() {
        return {
            isNavVisible: false,
        };
    },
    methods: {
        toggleMobileMenu() {
            this.isNavVisible = !this.isNavVisible;
        },
        handleResize() {
            if (window.innerWidth > 800) {
                this.isNavVisible = false; // 801px 이상이면 메뉴 닫기
            }
        },
        scrollLink(event) {
            event.preventDefault();

            const targetId = event.target.getAttribute("href");
            const targetElement = document.querySelector(targetId);

            if (targetElement) {
                targetElement.scrollIntoView({ behavior: "smooth" });
            }
        }
    },
    mounted() {
        window.addEventListener("resize", this.handleResize);
    },
    beforeUnmount() {
        window.removeEventListener("resize", this.handleResize);
    },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/mixin";

#header {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    z-index: 10000;
}

.hader__inner {
    display: flex;
    justify-content: space-between;
    align-items: center;
    /* background-color: rgba(116, 99, 99, 0.1); */
    /* backdrop-filter: blur(10px); */
    padding: 1rem;
}

.header__logo {
    font-size: 1rem;
    text-align: center;
    text-transform: uppercase;
    color: var(--black);
}

.header__logo em {
    font-weight: 400;
    font-size: 12px;
    padding: 4px 6px;
    border-radius: 4px;
    background-color: rgba(0, 0, 0, 0.2);
    margin-left: 8px;
}

.header__nav li {
    display: inline;
    cursor: pointer;
    color: var(--black);
}

.header__nav li a {
    display: inline-block;
    padding: 10px;
    text-transform: uppercase;
    position: relative;
    
}

.header__nav li a::before {
    content: '';
    width: calc(100% - 20px);
    height: 1px;
    background-color: var(--black);
    position: absolute;
    left: 10px;
    bottom: 4px;
    transform: scaleX(0);
    transition: transform 0.3s ease-in-out;
}

.header__nav li:hover a::before {
    transform: scaleX(1);
}

.header__nav__mobile {
    display: none;
    width: 40px;
    height: 40px;
    position: relative;
}

.header__nav__mobile span {
    display: flex;
    justify-self: center;
    width: 20px;
    height: 3px;
    background-color: var(--black);
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-20%, -50%);
    transition: all 0.3s;
}

.header__nav__mobile span::before {
    content: '';
    width: 30px;
    height: 3px;
    background-color: var(--black);
    position: absolute;
    right: 0;
    top: 10px;
    transition: all 0.3s;
}

.header__nav__mobile span::after {
    content: '';
    width: 30px;
    height: 3px;
    background-color: var(--black);
    position: absolute;
    right: 0;
    bottom: 10px;
    transition: width 0.3s;
    transition: all 0.3s;
}

@media (max-width: 800px) {
    .header__nav {
        display: none;
    }

    .header__nav.show {
        display: block;
    }

    .header__nav.show ul {
        display: block;
        position: absolute;
        padding: 20px 10px 20px 40px;
        right: 0;
        top: 68px;
        z-index: 10000;
    }

    .header__nav.show li {
        display: block;
        text-align: right;
    }

    .header__nav.show + .header__nav__mobile span {
        width: 30px;
        left: 49%;
        transform: translate(-49%, -50%);
    }

    .header__nav.show + .header__nav__mobile span::before {
        width: 20px;
    }

    .header__nav.show + .header__nav__mobile span::after {
        width: 20px;
    }

    .header__nav__mobile {
        display: block;
    }
}
</style>