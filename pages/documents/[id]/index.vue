<template >
    <div class="document">
        <div class="container document__inner ">
            <div class="breadcrumb">
                <span>Главная страница</span>

                <img src="~/assets/images/dot.svg" alt="youtube"/>

                <span>Документы</span>

                <img src="~/assets/images/dot.svg" alt="youtube"/>

                <span class="active">{{ targetDocument.title }}</span>
            </div>
            <h1 class="title-1">     
                {{ targetDocument.title }}
            </h1>

            <div class="document__content-block">
                <h1 class="title-1">Заголовок 1</h1>
                <p>
                    Представленная тележка-дозатор обеспечивает высококачественную обработку любых территорий сыпучими противогололедными реагентами самых разных типов, включая такие тяжелые, как гранитная и мраморная крошка, песок и пескосоляные смеси. Тележка прекрасно подходит для использования во дворах многоквартирных домов, обработки территорий промышленных предприятий, востребована владельцами магазинов, различных коммерческих компаний. Кроме того, она может использоваться для высева семян на газонах, теннисных кортах и других территориях. 
                    <br>
                    <br>
                    Представленная тележка-дозатор обеспечивает высококачественную обработку любых территорий сыпучими противогололедными реагентами самых разных типов, включая такие тяжелые, как гранитная и мраморная крошка, песок и пескосоляные смеси. 
                </p>
            </div>

            <div class="document__content-block">
                <h1 class="title-1">Заголовок 2</h1>
                <p>Представленная тележка-дозатор обеспечивает высококачественную обработку любых территорий сыпучими противогололедными реагентами самых разных типов, включая такие тяжелые, как гранитная и мраморная крошка, песок и пескосоляные смеси. </p>
            </div>

            <div class="document__content-block">
                <h1 class="title-1">Заголовок 3</h1>
                <p>
                    Представленная тележка-дозатор обеспечивает высококачественную обработку любых территорий сыпучими противогололедными реагентами самых разных типов, включая такие тяжелые, как гранитная и мраморная крошка, песок и пескосоляные смеси. Тележка прекрасно подходит для использования во дворах многоквартирных домов, обработки территорий промышленных предприятий, востребована владельцами магазинов, различных коммерческих компаний. Кроме того, она может использоваться для высева семян на газонах, теннисных кортах и других территориях. 
                    <br>
                    <br>
                    Представленная тележка-дозатор обеспечивает высококачественную обработку любых территорий сыпучими противогололедными реагентами самых разных типов, включая такие тяжелые, как гранитная и мраморная крошка, песок и пескосоляные смеси. 
                </p>
            </div>
        </div>
    </div>
</template>
<script setup>
import { computed } from 'vue';
import { useRoute } from 'vue-router';
import { documents } from '~/data/documents';

const route = useRoute()

const targetDocument = computed(() => {
    return documents.filter((item) => {
        return item.id == route.params.id
    })[0]
})

console.log(targetDocument)
</script>
