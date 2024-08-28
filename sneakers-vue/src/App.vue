<script setup>
import {onMounted, reactive, ref, watch} from "vue";
import axios from "axios";
import Header from "@/components/Header.vue";
import CardList from "@/components/CardList.vue";
import Drawer from "@/components/Drawer.vue";

const items = ref([]);

const filters = reactive({
    sortBy: 'title',
    searchQuery: '',
})

const onChangeSelect = event => {
    filters.sortBy = event.target.value;
}

const onChangeSearchInput = event => {
    filters.searchQuery = event.target.value;
}
const fetchItems = async () => {
    try {
        const params = {
            sortBy: filters.sortBy
        };

        if (filters.searchQuery) {
            params.title = `*${filters.searchQuery}*`
        }

        const {data} = await axios.get(
            `https://604781a0efa572c1.mokky.dev/items`, {
                params
            })
        items.value = data
        console.log(data)
    } catch (error) {
        console.log(error)
    }
}

onMounted(fetchItems);
watch(filters, fetchItems);
</script>

<template>
    <!--        <Drawer></Drawer>-->
    <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">
        <Header></Header>
        <div class="p-10">
            <div class="flex justify-between items-center">
                <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>
                <div class="flex gap-4">
                    <select @change="onChangeSelect" class="py-2 px-3 border rounded-mb outline-none">
                        <option value="name">По названию</option>
                        <option value="price">По цене (Дешевые)</option>
                        <option value="-price">По цене (Дорогие)</option>
                    </select>
                    <div class="relative">
                        <img class="absolute left-4 top-3" src="/search.svg" alt="search">
                        <input placeholder="Поиск..."
                               @change="onChangeSearchInput"
                               class="border rounded-md py-2 pl-11 pr-4 outline-none
                               focus:border-gray-400"
                               type="text"
                        />
                    </div>
                </div>
            </div>
            <div class="mt-10">
                <CardList :items="items"></CardList>
            </div>
        </div>
    </div>
</template>

<style scoped>

</style>
