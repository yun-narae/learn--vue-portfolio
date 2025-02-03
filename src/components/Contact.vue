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
                    <form @submit.prevent="sendEmail" id="contact__form" class="contact__form">
                        <div class="form__group name">
                            <label for="name">Name:</label>
                            <input v-model="formData.name" type="text" id="name" name="name" required />
                        </div>
                        <div class="form__group email">
                            <label for="email">Email:</label>
                            <input v-model="formData.email" type="email" id="email" name="email" required />
                        </div>
                        <div class="form__group message">
                            <label for="message">Message:</label>
                            <textarea v-model="formData.message" id="message" name="message" required></textarea>
                        </div>
                        <button type="submit">Send Message</button>
                        </form>
                </div>
            </div>            
        </section>
</template>

<script>
import emailjs from '@emailjs/browser';

export default {
  data() {
    return {
      formData: {
        name: '',
        email: '',
        message: '',
      },
    };
  },
  methods: {
    async sendEmail() {
      try {
        console.log("폼 제출 이벤트가 발생했습니다!");  // 이벤트 확인을 위한 로그

        // emailjs 초기화 (필요한 경우, 공개 키 설정)
        emailjs.init('uZwXD-cSyW-6lPXgf');  // 공개 키를 통해 초기화

        // 폼 요소를 가져옵니다.
        const form = document.getElementById('contact__form');
        // emailjs의 sendForm 메서드를 사용하여 이메일 전송
        const result = await emailjs.sendForm(
          'service_dvexwxl',  // 서비스 ID
          'template_hz7cr4x',  // 템플릿 ID
          form,    // 폼 ID
          'uZwXD-cSyW-6lPXgf'  // 공개 키
        );

        console.log('이메일 전송 성공:', result.text);
        alert('이메일이 성공적으로 전송되었습니다!');
      } catch (error) {
        console.log('이메일 전송 실패:', error.text);
        alert('이메일 전송에 실패했습니다.');
      }
    },
  },
};
</script>

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