<template>
    <section class="documents">
        <div class="container documents__inner">
            <h2 class="documents__title title-2">Документы</h2>
            <Swiper
                :modules="[SwiperNavigation, SwiperPagination]"
                :slides-per-view="1"
                :loop="true"
                :space-between="35"
                :navigation="true"
                class="documents__slider"
                :breakpoints="{
                    320: {
                        slidesPerView: 1,
                        spaceBetween: 20
                    },
                    480: {
                        slidesPerView: 1,
                        spaceBetween: 20
                    },
                    640: {
                        slidesPerView: 2,
                        spaceBetween: 30
                    },
                    992: {
                        slidesPerView: 3,
                    },

                }"
            >
                <SwiperSlide v-for="item in documents">
                    <div class="documents__slider-item slider-item">
                        <div class="slider-item__title">{{ item.title }}</div>
                        <div class="slider-item__text">{{ item.text }}</div>
                        <Button :variant="'primary'" @click="() => handleSliderItemClick(item.id)">Перейти</Button>
                    </div>
                </SwiperSlide>
                <SwiperSlide v-for="item in documents">
                    <div class="documents__slider-item slider-item">
                        <div class="slider-item__title">{{ item.title }}</div>
                        <div class="slider-item__text">{{ item.text }}</div>
                        <Button :variant="'primary'" @click="() => handleSliderItemClick(item.id)">Перейти</Button>
                    </div>
                </SwiperSlide>
            </Swiper>

        </div>
    </section>
</template>
<script setup lang="ts">
import { Swiper, SwiperSlide } from 'swiper/vue';
import { useRouter } from 'vue-router';
import { documents } from '@/data/documents'
import Button from './ui/Button.vue';

const router = useRouter()

const handleSliderItemClick = (id: number) => {
    router.push(`/documents/${id}`)
}
</script>
