<script setup>
    import { getToken } from '../../utils/helper';
    import Sidebar from '../Sidebar/Sidebar.vue';
    import { ref, onMounted, computed } from 'vue'

    const error = ref(null)
    const loading = ref(false)
    const API_URL = import.meta.env.VITE_API_URL
    const jadwal = ref([])
    const token = getToken()
    const ekskul = ref([])
    const ekskulList = computed(() => ekskul.value?.ekskulList)

    const dashboard = async () => {
        try{
            const res = await fetch(`${API_URL}/api/pembina/dashboard`, {
                headers: {
                    Authorization: `Bearer ${token}`
                }
            })

            const json = await res.json()
            ekskul.value = json.data

        }
        catch(err){
            error.value = err
        }
    }

    const schedule = async () => {
        try{
            const res = await fetch(`${API_URL}/api/schedule`, {
                headers: {
                    Authorization: `Bearer ${token}`
                }
            })

            const json = await res.json()
            jadwal.value = json.data
        }
        catch(err){
            error.value = err
        }
    }

    const formatTanggal = (dateString) => {
        const date = new Date(dateString)
        return date.toLocaleDateString('id-ID', {
            weekday: 'long',
            day: 'numeric',
            month: 'long',
            year: 'numeric'
        })
    }

    const createJadwal = async () => {
        try{
            const res = await fetch(`${API_URL}/api/pembina/schedule`, {
                method: 'POST',
                headers: {
                    "Content-Type": "application/json",
                    Authorization: `Bearer ${token}`
                },
                body: JSON.Stringfy({
                    title: title.value
                })
            })
        }
        catch(err){

        }
    }

    onMounted(() => {
        schedule(),
        dashboard()
    })
    
</script>

<template>
    <div>
        <Sidebar />

        <div class="p-10 ml-[16%]">

            <div class="grid grid-cols-2 gap-5"> 
                <!-- Form -->
                <div class="bg-white p-5 rounded-xl flex flex-col gap-5">
                    <div class="flex justify-center">
                        <h3 class="text-2xl font-bold">Buat Jadwal baru</h3>
                    </div>

                    <div v-if="ekskulList" class="">
                        <form @submit.prevent="createJadwal" class="flex flex-col gap-5">
                            <div class="shadow-md">
                                <select class="border-2 border-gray-400/50 rounded-md w-full py-3 pl-5">
                                    <option>-- Select Ekskul --</option>
                                    <option v-for="e in ekskulList" :key="e.id" :value="e.id">{{ e.name }}</option>
                                </select>
                            </div>
                            <div class="shadow-md">
                                <input v-model="title" class="border-2 border-gray-400/50 rounded-md w-full py-3 pl-5" placeholder="Masukkan Nama Kegiatan">
                            </div>
                            <div class="shadow-md">
                                <textarea v-model="description" class="border-2 border-gray-400/50 rounded-md w-full py-5 pl-5 pr-5" placeholder="Masukkan Description Kegiatan"></textarea>
                            </div>
                            <div class="shadow-md">
                                <input v-model="scheduleDate" type="date" class="border-2 border-gray-400/50 rounded-md w-full py-3 pl-5 pr-5">
                            </div>
                            <div class="shadow-md">
                                <input v-model="location" class="border-2 border-gray-400/50 rounded-md w-full py-3 pl-5" placeholder="Masukkan Lokasi Kegiatan">
                            </div>
                            <div class="shadow-md">
                                <button class="bg-blue-800 text-white font-semibold text-center rounded-md w-full py-3">Buat Jadwal</button>
                            </div>
                        </form>
                    </div>
                </div>

                <!-- Jadwal -->
                <div class="bg-white p-5 rounded-xl flex flex-col gap-7">
                    <div class="flex justify-center">
                        <h3 class="text-2xl font-bold">Jadwal Ekskul yang Akan Datang</h3>
                    </div>
                    <div v-if="jadwal" class="max-h-[500px] overflow-y-auto pr-5 pl-5">
                        <div v-for="s in jadwal" class="border-b border-gray-400/50 pb-3" :key="s.id">
                            <h3 class="text-blue-500 font-bold capitalize">{{ s.title }}</h3>
                            <h3 class="text-sm">{{ formatTanggal(s.scheduleDate) }}</h3>
                            <h3 class="text-sm">{{ s.location }}</h3>
                            <h3 class="text-sm text-gray-400">{{ s.extracurricular.name }}</h3>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

</template>

<style scoped></style>