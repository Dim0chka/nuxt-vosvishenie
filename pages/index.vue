<template>
    <section class="main-block">
        <div class="container main-center">
            <h1>Строительная компания "Воздвижение"</h1>
            <p>Надежная компания с большим опытом на рынке строительства</p>
            <nuxt-link :to="{ path: '/',hash:'#project'}">Наши проекты</nuxt-link>
        </div>
    </section>
    <section id="advantages" class="main-advantages">
        <div class="container">
            <div class="flex-advantages">

                <div class="card" v-for="item in cards" :key="item.id">
                    <div :style="{ backgroundImage: `url(${item.img})` }" class="image">
                        <div class="icon">
                            <img :src=" '/logo/' + item.icon " alt="">
                        </div>
                    </div>
                    <div class="content-card">
                        <h3>{{ item.title }}</h3>
                        <span>{{ item.text }}</span>
                    </div>
                </div>

            </div>
        </div>
    </section>
    <section id="project" class="main-project">
        <div class="container">
            <h2 class="title-project">Наши проекты</h2>
            <div class="project-flex">

                <div class="card-project" v-for="item in sliceProject">
                    <nuxt-link class="card-project-img" to="/">
                        <div :style="{ backgroundImage: `url(${item.img})`}"></div>
                    </nuxt-link>
                    <nuxt-link to="/">
                        <h3>{{ item.name }}</h3>
                    </nuxt-link>
                </div>

            </div>
        </div>
    </section>
    <section id="clients" class="main-clients">
        <div class="container">
            <h2 class="title-clients">Нам доверяют клиенты</h2>
            <div class="clients-flex">
                <div class="card-clients" v-for="client in clients">
                    <img :src=" '/logo/' +  client.logo " alt="" height="80">
                </div>
            </div>
        </div>
    </section>
    <iframe class="map" src="https://yandex.ru/map-widget/v1/?um=constructor%3Ae9f7b2f8e7d170a93ed029d5a200bab3667e74db0054e13bd2d6ac4b367353b2&amp;source=constructor" frameborder="0"></iframe>
    <section id="contact" class="main-contacts">
        <div class="container">
            <div class="flex-contacts">

                <div class="contact-card" v-for="contact in contacts">
                    <h3>{{contact.title}}</h3>
                    <nuxt-link :to="contact.to">
                        {{ contact.contact }}
                    </nuxt-link>
                </div>

            </div>
        </div>
    </section>
</template>

<script setup>
import {ref, computed} from 'vue'

const cards = [
    {
        icon: 'rub.svg',
        title: 'финансовая прозрачность',
        text: 'В основе которой лежат наши приоритеты: ответственность и честность. Доверяя свой проект нам, Вы может быть уверены в рациональном и целевом использовании денежных средст.', 
        img: '/image/front-advantage-1.jpg'
    },
    {
        icon: 'brick.svg',
        title: 'качественные  стройматериалы',
        text: 'Обеспечивают непревзойденный результат и безопасность строительства. Все используемые нами материалы имеют сертификаты соответствия международным стандартам. Мы заботимся о Вас и окружающей среде.',
        img: '/image/front-advantage-2.jpg'
    },
    {
        icon: 'technique.svg',
        title: 'собственная техническая база',
        text: 'Позволяет слаженно и эффективно выполнять поставленные задачи. Отсутствие посредников дает возможность минимизировать издержки и экономит время.',
        img: '/image/front-advantage-3.jpg'
    },
]

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

const clients = [
    {logo: 'client-1.png', alt: 'client-1'},
    {logo: 'client-2.jpg', alt: 'client-2'},
    {logo: 'client-3.png', alt: 'client-3'},
    {logo: 'client-4.png', alt: 'client-4'},
    {logo: 'client-5.jpg', alt: 'client-5'},
    {logo: 'client-6.png', alt: 'client-6'},
    {logo: 'client-7.png', alt: 'client-7'},
    {logo: 'client-8.png', alt: 'client-8'}
]

const contacts = [
    {title: 'Контактные телефоны', contact: '+7 (495) 783-68-53', to: 'tel:74957836853'},
    {title: 'Электронная почта', contact: 'info@vzdv.ru', to: 'mailto:info@vzdv.ru'},
    {title: 'Юридический адрес', contact: '117218, г. Москва, ул. Кржижановского, д. 15, корп. 5, эт. 5, пом. 517В, оф. 1', to: 'https://yandex.ru/maps/-/CDUTfZ14'},
    {title: 'Почтовый адрес', contact: '125252, г. Москва, ул. Куусинена, д. 21Б, оф. 318', to: 'https://yandex.ru/maps/-/CDUTfZpG'}
]

const sliceProject = computed(() => {
  return project.value.slice(0, 6)
})


</script>

<style lang="scss">
.main-block {
    margin-top: 35px;

    display: block;
    background: url('/image/front-page-banner-1.jpg') no-repeat center / cover;
    width: 100%; 

    @media only screen and (max-width: 1279px) {
        margin-top: 0;
    }

    .main-center {
        height: 550px;
        display: flex;
        justify-content: center;
        flex-direction: column;
        text-align: center;
        align-items: center;

        color: $text-header;

        @media only screen and (max-width: 767px) {
            height: 440px;
        } 

        & > h1 {
            font-family: "Montserrat", "Arial", sans-serif;
            font-weight: 500;
            text-transform: uppercase;
            font-size: 40px;

            @media only screen and (max-width: 767px) {
                font-size: 28px;
            }
        }

        & > p {
            font-family: "PT Sans";
            font-size: 18px;
            font-weight: bold;

            margin-bottom: 20px;
        }

        & > a {
            background-color: $bg;
            color: $text-header;

            display: inline-block;
            padding: 12px 35px;
            font-family: "Montserrat", "Arial", sans-serif;
            font-weight: 500;
            text-align: center;
            text-decoration: none;
            text-transform: uppercase;
            border-radius: 3px;
            -webkit-transition: background-color 0.25s;
            transition: background-color 0.25s;
            cursor: pointer;

            &:hover {
                background-color: $bg-hover;
            }
        }
    }
}

.main-advantages {
    padding: 70px 0 50px 0;

    background-color: $bg-advantages;

    .flex-advantages {
        display: flex;
        flex-direction: row;
        justify-content: space-between;

        gap: 20px;

        width: 100%;

        @media only screen and (max-width: 1279px) {
            flex-direction: column;
        }

        .card {
            background-color: $text-header;
            text-align: center;

            width: 100%;

            .image {
                position: relative;
                height: 250px;
                margin-bottom: 50px;
                background-repeat: no-repeat;
                background-position: center;
                background-size: cover;

                .icon {
                    background-color: $bg;

                    position: absolute;
                    bottom: -40px;
                    left: calc(50% - 40px);
                    display: -webkit-box;
                    display: flex;
                    -webkit-box-pack: center;
                    justify-content: center;
                    -webkit-box-align: center;
                    align-items: center;
                    width: 80px;
                    height: 80px;
                    border-radius: 50%;
                    box-shadow: 0 0 9px 2px rgba(0, 0, 0, 0.1);
                }
            }

            .content-card {
                padding: 0 28px 40px 28px;

                h3 {
                    margin-bottom: 16px;
                    font-size: 17px;
                    color: $title;
                    text-transform: uppercase;

                    &::after {
                        content: "";
                        margin-left: calc( 50% - 18.5px);
                        display: block;
                        width: 37px;
                        height: 3px;
                        margin-top: 16px;

                        background-color: $bg;
                    }
                }

                p {
                    color: $text-color2;
                }
            }
        }
    }
}

.main-project {
    padding: 60px 0 50px 0;


    .title-project {
        color: $title;
        font-size: 22px;
        font-weight: 500;
        text-transform: uppercase;
        margin-bottom: 30px;
        text-align: center;
    }

    .project-flex {
        display: flex;
        flex-wrap: wrap;
        width: 100%;


        gap: 40px 20px;

        .card-project {
            max-width: calc((100% - 20px * 2) / 3);
            width: 100%;

            @media only screen and (min-width: 768px) and (max-width: 1279px) {
                max-width: calc((100% - 20px) / 2);
            }

            @media only screen and (max-width: 767px) {
                max-width: 100%;
            }

            .card-project-img {
                display: block;

                position: relative;
                height: 270px;
                margin-bottom: 20px;
                overflow: hidden;
    
                &::before, &::after {
                    content: "";
                    position: absolute;
                    z-index: 10;
                    top: 0;
                    left: 0;
                    display: block;
                    width: 100%;
                    height: 100%;
                }
    
                &::before {
                    background-color: rgba(0, 0, 0, 0);
                    -webkit-transition: background-color 0.25s;
                    transition: background-color 0.25s;
                }
    
                &::after {
                    background-image: url('/logo/chain.svg');
                    background-repeat: no-repeat;
                    background-position: center;
                    opacity: 0;
                    -webkit-transition: opacity 0.25s;
                    transition: opacity 0.25s;
                }
    
                &:hover > div {
                    transform: scale(1.1);
                }
    
                &:hover::before {
                    background-color: rgba(0, 0, 0, 0.5);
                }
    
                &:hover::after {
                    opacity: 1;
                }
    
                & > div {
                    width: 100%;
                    height: 100%;
                    background-repeat: no-repeat;
                    background-position: center;
                    background-size: cover;
                    -webkit-transition: -webkit-transform 0.25s;
                    transition: -webkit-transform 0.25s;
                    transition: transform 0.25s;
                    transition: transform 0.25s, -webkit-transform 0.25s;
                    
                }
                
            }

            a {
                text-align: center;
                display: block;
                color: $title;

                font-family: "Montserrat";

                &:hover {
                    color: $bg;
                    text-decoration: none;
                }

                h3 {
                    font-size: 17px;
                    text-transform: uppercase;

                }
            }

        }

    }
}

.main-clients {
    background-color: $bg-advantages;
    padding: 50px 0 30px 0;

    .title-clients {
        color: $title;
        font-size: 22px;
        font-weight: 500;
        text-transform: uppercase;
        margin-bottom: 30px;
        text-align: center;
    }

    .clients-flex {
        display: flex;
        flex-wrap: wrap;
        width: 100%;

        gap: 20px;

        .card-clients {
            background-color: $text-header;
            max-width: calc((100% - 20px * 3) / 4);
            width: 100%;
            display: flex;
            -webkit-box-pack: center;
            justify-content: center;
            -webkit-box-align: center;
            align-items: center;
            height: 110px;

            @media only screen and (min-width: 768px) and (max-width: 1279px) {
                max-width: calc((100% - 20px) / 2);
            }

            @media only screen and (max-width: 767px) {
                max-width: 100%;
            }
        }
    }
}

.map {
    width: 100%;
    height: 450px;
    margin-bottom: 60px;

    @media only screen and (max-width: 767px) {
        height: 350px;
    }
}

.main-contacts {
    width: 100%;

    .flex-contacts {
        display: flex;
        flex-wrap: wrap;

        gap: 20px;

        .contact-card {
            width: 100%;
            max-width: calc((100% - 20px * 3) / 4);
            display: inline-block;

            @media only screen and (min-width: 768px) and (max-width: 1279px) {
                max-width: calc((100% - 20px) / 2);
            }

            @media only screen and (max-width: 767px) {
                max-width: 100%;
            }

            h3 {
                font-size: 17px;
                text-transform: uppercase;
                color: $title;

                margin-bottom: 20px;
            }
        }
    }
}
</style>