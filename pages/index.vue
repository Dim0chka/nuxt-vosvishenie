<template>
    <section class="main-block">
        <div class="container main-center">
            <h1>Строительная компания "Воздвижение"</h1>
            <p>Надежная компания с большим опытом на рынке строительства</p>
            <nuxt-link to="">Наши проекты</nuxt-link>
        </div>
    </section>
    <section class="main-advantages">
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
    <section class="main-project">
        <div class="container">
            <h2 class="title-project">Наши проекты</h2>
            <div class="project-flex">

                <div class="card-project" v-for="item in sliceProject">
                    <nuxt-link class="card-project-img" to="">
                        <div :style="{ backgroundImage: `url(${item.img})`}"></div>
                    </nuxt-link>
                    <nuxt-link to="">
                        <h3>{{ item.name }}</h3>
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
    padding-top: 60px;


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

            @media only screen and (min-width: 375px) and (max-width: 767px) {
                max-width: 100%;
            }

            @media only screen and (max-width: 374px) {
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

                font-family: "Montserrat";

                &:hover {
                    text-decoration: none;
                }

                h3 {
                    -webkit-transition: color 0.25s;
                    transition: color 0.25s;
                    font-size: 17px;
                    text-transform: uppercase;
                }
            }

        }

    }
}
</style>