<script setup>
import Header from "@/components/Header.vue";
import CardList from "@/components/CardList.vue";
import Drawer from "@/components/Drawer.vue";


</script>

<template>
    <!--    <Drawer></Drawer>-->
    <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">
        <Header></Header>
        <div class="p-10">
            <div class="flex justify-between items-center">
                <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>
                <div class="flex gap-4">
                    <select class="py-2 px-3 border rounded-mb outline-none">
                        <option>По названию</option>
                        <option>По цене (Дешевые)</option>
                        <option>По цене (Дорогие)</option>
                    </select>
                    <div class="relative">
                        <img class="absolute left-4 top-3" src="/search.svg" alt="search">
                        <input placeholder="Поиск..."
                               class="border rounded-md py-2 pl-11 pr-4 outline-none
                    focus:border-gray-400"
                               type="text"
                        />
                    </div>
                </div>
            </div>
            <CardList></CardList>
        </div>
    </div>
</template>

<style scoped>

</style>
