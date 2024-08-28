<script setup>
import Card from "./Card.vue";

const onClickAdd = () => {
    alert('Добавить')
}

defineProps({
    items: Array
})
</script>

<template>
    <div class="grid grid-cols-4 gap-5">
        <Card
            v-for="item in items"
            :key="item.id"
            :title="item.title"
            :image-url="item.imageUrl"
            :price="item.price"
            :is-favorite="false"
            :on-click-add="onClickAdd"
        />
    </div>
</template>
