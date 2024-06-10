<template>
    <div class="hero">
        <div class="container hero__inner">
            <div class="hero__content">
                <div class="hero__title title-1">Проверьте штрафы и зарегестрируйтесь в 1 клик</div>
                <form class="hero__form"  @submit.prevent="submit">
                  <div class="hero__inputs-row">
                    <Input 
                      class="hero__input-number" 
                      label="Номер автомобиля"
                      v-model="carNumber"
                      name="carNumber"
                      :error="errorCarNumber" 
                      />
                    <Input 
                      class="hero__input-region" 
                      label="Регион" 
                      v-model="region"
                      name="region"
                      :error="errorRegion" 
                    />
                  </div>
                  <Input 
                    class="hero__input-certificate" 
                    label="Свидетельство о регистрации ТС" 
                    v-model="certificate"
                    name="certificate"
                    :error="errorCertificate" 
                  />
                  <div class="hero__actions">
                    <Button :variant="'primary'">
                        Проверить штрафы
                        <img src="~/assets/images/arrow-right.svg" alt="arrow-right"/>
                    </Button>
                    <Button :variant="'secondary'" type="button"  @click="openModal">
                        <img src="~/assets/images/youtube.svg" alt="youtube"/>
                        О сервисе
                        <span style="color: #1253A2;">(1 мин. 20 сек)</span>
                    </Button>
                  </div>
                  <p class="hero__agreement">Нажимая «Проверить штрафы» вы соглашаетесь с политикой обработки персональных данных и принимаете оферту</p>
                </form>
            </div>
            <div class="hero__image">
                <img src="~/assets/images/hero-image.svg" alt="hero-image">
            </div>

            <div v-if="isModalOpen" class="modal-overlay" @click="closeModal">
                <div class="modal" @click.stop>
                    <iframe
                    src="https://www.youtube.com/embed/YE7VzlLtp-4"
                    frameborder="0"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                    allowfullscreen
                    ></iframe>
                    <button class="modal-close-button" @click="closeModal">
                        <img src="~/assets/images/close.svg" alt="close">
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>
<script setup lang="ts">
import { ref } from 'vue';
import { toast } from 'vue3-toastify';
import { useField, useForm } from 'vee-validate';
import * as yup from 'yup';
import Button from '../ui/Button.vue';
import Input from '../ui/Input.vue';

const isModalOpen = ref(false)

const openModal = () => {
    isModalOpen.value = true
}

const closeModal = () => {
    isModalOpen.value = false
}

const schema = yup.object({
  carNumber: yup.string().required('Пожалуйста, введите Номер автомобиляя').trim(),
  region: yup.string().required('Пожалуйста, введите Регион').trim(),
  certificate: yup.string().required('Свидетельство о регистрации ТС').trim(),
});

const { handleSubmit } = useForm({
  validationSchema: schema,
});

const { value: carNumber, errorMessage: errorCarNumber } = useField('carNumber');
const { value: region, errorMessage: errorRegion } = useField('region');
const { value: certificate, errorMessage: errorCertificate } = useField('certificate');

const submit = handleSubmit((values) => {
  toast.success('Форма отправлена!')
});


</script>