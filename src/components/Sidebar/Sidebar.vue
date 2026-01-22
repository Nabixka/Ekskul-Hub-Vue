<script setup>
import { ref } from 'vue'

const isOpen = ref(false)

const Handleopen = () => {
    isOpen.value = !isOpen.value
}

</script>

<template>
        <!-- Large -->
        <div class="lg:flex hidden fixed top-0 left-0 h-screen bg-blue-800 flex-col h-screen w-1/5 justify-center gap-8 pl-5 pr-5">
            <router-link active-class="!text-black bg-yellow-400 text-black rounded-md"
                class="text-white flex pl-2 py-2 items-center gap-3" to="/home">
                <i class="pi pi-home text-lg font-semibold"></i>
                <h3 class="font-semibold text-lg">Home</h3>
            </router-link>
            <router-link active-class="!text-black bg-yellow-400 text-black rounded-md"
                class="text-white flex pl-2 py-2 items-center gap-3" to="/jadwal">
                <i class="pi pi-clipboard text-lg font-semibold"></i>
                <h3 class="font-semibold text-lg">Buat Jadwal</h3>
            </router-link>
            <router-link active-class="!text-black bg-yellow-400 text-black rounded-md"
                class="text-white flex pl-2 py-2 items-center gap-3" to="/dokumentasi">
                <i class="pi pi-folder text-lg font-semibold"></i>
                <h3 class="font-semibold text-lg">Dokumentasi</h3>
            </router-link>
            <router-link active-class="!text-black bg-yellow-400 text-black rounded-md"
                class="text-white flex pl-2 py-2 items-center gap-3" to="/absen">
                <i class="pi pi-list-check text-lg font-semibold"></i>
                <h3 class="font-semibold text-lg">Absensi</h3>
            </router-link>
        </div>
    
        <!-- Small - Medium -->
        <div class="lg:hidden bg-blue-800 w-full py-2">
            <div class="flex justify-between">
                <h3 class="pl-5 text-white">Ekskul-Hub</h3>
                <button @click="Handleopen">
                    <i class="text-white pi pi-list pr-5 font-bold text-2xl"></i>
                </button>
            </div>
            <div v-if="isOpen" class="mt-3 ml-5 mr-5 mb-2 flex flex-col gap-3">
                <div class="border-b w-full border-white"></div>
                <router-link active-class="bg-yellow-400 !text-black" class="text-white rounded-md py-2 flex justify-center" to="/home">
                    <h3 class="font-bold">Home</h3>
                </router-link>
                <router-link active-class="bg-yellow-400 !text-black" class="text-white rounded-md py-2 flex justify-center" to="/jadwal">
                    <h3 class="font-bold">Jadwal</h3>
                </router-link>
                <router-link active-class="bg-yellow-400 !text-black" class="text-white rounded-md py-2 flex justify-center" to="/dokumentasi">
                    <h3 class="font-bold">Dokumentasi</h3>
                </router-link>
                <router-link active-class="bg-yellow-400 !text-black" class="text-white rounded-md py-2 flex justify-center" to="/absen">
                    <h3 class="font-bold">Absensi</h3>
                </router-link>
            </div>
        </div>

</template>

<style scoped></style>
