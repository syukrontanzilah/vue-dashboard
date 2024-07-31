<script lang="ts" setup>
import { ref } from 'vue';
const open = ref(false);
</script>

<template>
    <div class="">
        <div class="flex z-50 items-center justify-between w-full h-full p-4 lg:hidden shadow-sm">
            <Logo/>
            <Icon 
            class="z-50 cursor-pointer left-2 top-2" size="30" 
            name="tabler:menu-2"
            @click="open = true"
            />
            <div v-if="open" class="fixed top-0 left-0 z-50 w-full h-screen bg-white">
                <Icon 
            class="absolute z-50 cursor-pointer right-4 top-4" size="30" 
            name="material-symbols:close"
            @click="open = false"
            />
                <SidebarMenu/>
            </div>
        </div>
        <div class="hidden lg:flex w-[250px] h-screen  flex-col justify-between border-r">
            <SidebarMenu/>
            <div>
                user item
            </div>
        </div>
    </div>
</template>
