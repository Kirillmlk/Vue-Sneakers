<script setup>
import Card from "./Card.vue";

defineProps({
    items: Array,
})

const emit = defineEmits(['addToFavorite']);

</script>

<template>
    <div class="grid grid-cols-4 gap-5">
        <Card
            v-for="item in items"
            :key="item.id"
            :id="item.id"
            :title="item.title"
            :image-url="item.imageUrl"
            :price="item.price"
            :is-favorite="false"

            :on-click-favorite="() => emit('addToFavorite', item)"
            :isFavorite="item.isFavorite"
        />
    </div>
</template>
//:on-click-add="onClickAdd"