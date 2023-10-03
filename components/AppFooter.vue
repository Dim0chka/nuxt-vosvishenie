<template>
    <footer class="footer">
        <section class="footer-layout">
            <div class="container">
                <div class="footer-content flex-footer">
                    <div class="flex-footer">

                        <div class="widget-footer">
                            <h3>О компании</h3>
                            <nuxt-link class="logo" to="/">
                                <img src="/logo/logo2.svg" alt="">
                            </nuxt-link>
                            <p>
                                Воздвижение - активно развивающаяся компания с крепким репутационным авторитетом на рынке столицы.
                            </p>
                        </div>
    
                        <div class="widget-footer">
                            <h3>Контакты</h3>
                            <nav class="footer-contact">
                                <nuxt-link to="tel:74957836853">
                                +7 (495) 783-68-53
                                </nuxt-link>
                                <nuxt-link  to="mailto:info@vzdv.ru">
                                    info@vzdv.ru
                                </nuxt-link>
                                <nuxt-link to="https://yandex.ru/maps/-/CDU9UMLk">
                                    117218, г. Москва, ул. Кржижановского, д. 15, корп. 5, эт. 5, пом. 517В, оф. 1
                                </nuxt-link>
                            </nav>
                        </div>
    
                        <div class="widget-footer">
                            <h3>Меню</h3>
                            <div class="footer-nav">
                                <nuxt-link :to="{ path: '/', hash: ''}">
                                    Главная
                                </nuxt-link>
                                <nuxt-link :to="{ path: '/', hash: '#project'}">
                                    Проекты
                                </nuxt-link>
                                <nuxt-link :to="{ path: '/', hash: '#advantages'}" >
                                    Преимущества
                                </nuxt-link>
                                <nuxt-link :to="{ path: '/', hash: '#clients'}">
                                    Клиенты
                                </nuxt-link>
                                <nuxt-link :to="{ path: '/', hash: '#contacts'}">
                                    Контакты
                                </nuxt-link>
                            </div>
                        </div>
    
                        <div class="widget-footer">
                            <h3>Проекты</h3>
                            <div class="footer-nav">
                                <nuxt-link :to="{ path: '/', hash: '#project'}" v-for="project in projectSlice">
                                    {{ project.name }}
                                </nuxt-link>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        <section class="copyright"> 
            <div class="container">
                2021 © ООО "Воздвижение" • ИНН 7703428441 • КПП 1177746558186 • ОГРН 1177746558186 • Политика конфиденциальности
            </div>
        </section>
    </footer>
</template>


<script setup>
import {ref, computed} from 'vue'

const project = ref([
    {id: 1, img: '/image/banner-1.jpg', name: 'Пристройка на 200 мест к зданию МОУ СОШ №17'},
    {id: 2, img: '/image/banner-2.jpg', name: 'Улица Зайцева и Москворецкая набережная'},
    {id: 3, img: '/image/banner-3.jpg', name: 'ФОК с плавательным бассейном, го Серебряные Пруды'},
    {id: 4, img: '/image/banner-4.jpg', name: 'Часовня Св. Александра Невского'},
    {id: 5, img: '/image/banner-5.jpg', name: 'Благоустройство ул. Ремесленной, го Серебряные Пруды, Уч. №5'},
    {id: 6, img: '/image/banner-6.jpg', name: 'Работы по повышению безопасности дор. движ., РУАД № 5'},
    {id: 7, img: '/image/banner-6.jpg', name: 'Работы по повышению безопасности дор. движ., РУАД № 5'},
    {id: 8, img: '/image/banner-6.jpg', name: 'Работы по повышению безопасности дор. движ., РУАД № 5'}
])

const projectSlice = computed(() => {
    return project.value.slice(0, 3)
})

</script>


<style lang="scss">
.footer {
    margin-top: 70px;

    .footer-layout {
        width: 100%;
        background-color: $bg-footer1;

        .footer-content {
            padding: 60px 0;

            .flex-footer {
                display: flex;
                flex-wrap: wrap;

                gap: 20px;

                @media only screen and (max-width: 1279px) {
                    gap: 30px 20px;
                }

                .widget-footer {
                    max-width: calc((100% - 20px * 3) / 4);
                    width: 100%;

                    @media only screen and (min-width: 768px) and (max-width: 1279px) {
                        max-width: calc((100% - 20px) / 2);
                    }

                    @media only screen and (max-width: 767px) {
                        max-width: 100%;
                    }
                    
                    h3 {
                        margin-bottom: 40px;
                        font-size: 17px;
                        color: $text-header;
                        text-transform: uppercase;
    
                        &::after {
                            content: "";
                            margin-right: calc( 50% - 18.5px);
                            display: block;
                            width: 37px;
                            height: 3px;
                            margin-top: 14px;
    
                            background-color: $bg;
                        }
                    }

                    .logo {
                        display: block;
                        margin-bottom: 10px;
                    }

                    p {
                        color: $text;
                    }

                    .footer-contact {
                        display: flex;
                        flex-direction: column;
                        gap: 12px;
                    }

                    .footer-nav {
                        display: flex;
                        flex-direction: column;

                        a {
                            position: relative;
                            display: inline-block;
                            padding: 4px 18px;
                            border-bottom: 1px solid #3a3a3a;

                            &::before {
                                content: "";
                                position: absolute;
                                top: 50%;
                                left: 0;
                                display: block;
                                width: 5px;
                                height: 8px;
                                background: url('/logo/arrow.svg') no-repeat center;
                                -webkit-transform: translateY(-50%);
                                transform: translateY(-50%);
                            }

                            &:hover {
                                text-decoration: none;
                            }
                        }
                    }
                }   
            }
        }
    }

    .copyright {
        padding: 12px 0;
        text-align: center;
        background-color: $bg-footer2;
        color: $text-color2;
        font-family: 'PT Sans';
    }
}

</style>