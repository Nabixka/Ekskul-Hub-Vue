<script setup>
    import { ref } from 'vue'

    const isOpen = ref(false)

    const Handleopen = () => {
        isOpen.value - !isOpen.value
    }

</script>

<template>
    <div class="fixed top-0 left-0 h-screen bg-blue-800 flex flex-col h-screen w-1/6 justify-center gap-8 pl-5 pr-5">
        <router-link active-class="!text-black bg-yellow-400 text-black rounded-md" class="text-white flex pl-2 py-2 items-center gap-3" to="/home">
            <i class="pi pi-home lg:text-xl font-semibold"></i>
            <h3 class="font-semibold lg:text-xl">Home</h3>
        </router-link>
        <router-link active-class="!text-black bg-yellow-400 text-black rounded-md" class="text-white flex pl-2 py-2 items-center gap-3" to="/jadwal">
            <i class="pi pi-clipboard lg:text-xl font-semibold"></i>
            <h3 class="font-semibold lg:text-xl">Buat Jadwal</h3>
        </router-link>
        <router-link active-class="!text-black bg-yellow-400 text-black rounded-md" class="text-white flex pl-2 py-2 items-center gap-3"  to="/dokumentasi">
            <i class="pi pi-folder lg:text-xl font-semibold"></i>
            <h3 class="font-semibold lg:text-xl">Dokumentasi</h3>
        </router-link>
        <router-link active-class="!text-black bg-yellow-400 text-black rounded-md" class="text-white flex pl-2 py-2 items-center gap-3" to="/absen">
            <i class="pi pi-list lg:text-xl font-semibold"></i>
            <h3 class="font-semibold lg:text-xl">Absensi</h3>
        </router-link>
    </div>
</template>

<style scoped></style>
