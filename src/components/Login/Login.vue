<script setup>
</script>

<template>

    <div class="flex justify-between overflow-hidden">

        <!-- Form  -->
        <div class="flex flex-col justify-center h-screen gap-5 pl-20 w-100">
            <div>
                <h3 class="text-4xl font-bold">Login</h3>
            </div>
            <form class="flex flex-col gap-5">
                <div class="flex flex-col gap-5">
                    <div class="w-full">
                        <input class="w-full pl-2 bg-gray-100/90 rounded-md py-2" type="email" placeholder="Masukkan Email">
                    </div>
                    <div class="w-full">
                        <input class="w-full pl-2 bg-gray-100/90 rounded-md py-2" type="text" placeholder="Masukkan Password">
                    </div>
                </div>
                <div class="flex justify-end">
                    <button
                        class="text-white font-semibold bg-linear-to-b from-blue-800 to-blue-500 w-2/5 py-1 rounded-md">Login</button>
                </div>
            </form>
        </div>

        <!-- Circle -->
        <div class="relative h-screen w-175 left-50">
            <div class="absolute left-0 top-0 bg-cyan-500 w-175 h-full rounded-full"></div>
            <div class="absolute left-20 top-0 bg-cyan-600 w-175 h-full rounded-full"></div>
            <div class="absolute left-40 top-0 bg-cyan-700 w-175 h-full rounded-full"></div>
        </div>

    </div>

</template>

<style scoped></style>
