<script setup>
import { contactText } from "../constants";
</script>

<template>
    <section id="contact">
            <div class="contact__inner">
                <h2 class="contact__title">contact</h2>
                <div class="contact__wrap">
                    <div class="contact__text">
                        <div class="text" v-for="(contact, key) in contactText" :key="key">
                            <div>
                                <a :href="contact.link" target="_blank">{{contact.title}}</a>
                            </div>
                        </div>
                    </div>
                    <form id="contact__form" class="contact__form" action="#">
                        <fieldset>
                            <div class="form__group name">
                                <label for="name">Name</label>
                                <input type="text" id="name" name="name" placeholder="Your name" required />
                            </div>
                    
                            <div class="form__group email">
                                <label for="email">Email</label>
                                <input type="email" id="email" name="email" placeholder="Your email" required />
                            </div>
                    
                            <div class="form__group message">
                                <label for="message">Message</label>
                                <textarea id="message" name="message" placeholder="Your message" required></textarea>
                            </div>
                        </fieldset>
                    
                        <button type="submit">Submit</button>
                    </form>
                </div>
            </div>            
        </section>
</template>

<style lang="scss" scoped>
    .contact__inner {
    margin: 10vh 0;
    padding: 0 16px;
}

.contact__title {
    width: 100%;
    height: 10%;
    font-size: 24px;
    font-weight: 700;
    text-transform: uppercase;
    word-break: keep-all;
    border-bottom: 1px solid var(--black);
    background-color: var(--mainBg-color);
    margin-bottom: 30px;
}

.contact__wrap {
    display: grid;
    grid-template-columns: 1fr 1fr;
}

.contact__text {
    font-size: 1rem;
    font-weight: 700;
}

.contact__form fieldset {
    border: none;
    padding: 0;
    margin: 0;
}

.contact__form .form__group {
    margin-bottom: 20px;
    display: flex;
    flex-wrap: wrap;
}

.contact__form .form__group label {
    display: block;
    font-size: 1rem;
    font-weight: bold;
    margin-bottom: 5px;
    color: var(--black100);
}

.contact__form .form__group input,
.contact__form .form__group textarea {
    width: 100%;
    padding: 10px;
    font-size: 1rem;
    border: 1px solid var(--subBg100);
    border-radius: 4px;
    background-color: var(--mainBg-color);
    color: #333;
}

.contact__form .form__group input:focus,
.contact__form .form__group textarea:focus {
    border-color: #007bff;
    outline: none;
    border: 1px solid var(--subBg300);
}

.contact__form textarea {
    height: 150px;
    resize: vertical;
}

/* 제출 버튼 스타일 */
.contact__form button[type="submit"] {
    padding: 10px 20px;
    font-size: 1rem;
    color: #fff;
    background-color: var(--subBg300);
    border: none;
    border-radius: 4px;
    cursor: pointer;
    width: 100%;
    margin-top: 10px;
}

.contact__form button[type="submit"]:hover {
    background-color: var(--black300);
}

.contact__form button[type="submit"]:active {
    background-color: var(--black100);
}

@media (max-width: 800px) {
    .contact__wrap {
        grid-template-columns: none;
    }

    .contact__text {
        margin-bottom: 40px;
    }
}
</style>