<script lang="ts" setup>
const items = ref([
    { title: "Overview", path:'/', icon:'tabler:layout-dashboard-filled'},
    { title: "Transactions", path:'/transactions', icon:'icon-park-solid:transaction'},
    { title: "Account", path:'/account', icon:'material-symbols:account-circle'},
    { title: "Contacts", path:'/contacts', icon:'mage:contact-book-fill'},
    { title: "Settings", path:'/settings', icon:'icon-park-solid:setting-two'},
])
</script>

<template>
    <div>
        <header class="flex items-center gap-2 p-4 hover:scale-[101%] transition cursor-pointer">
            <Logo/>
            <p class="font-bold font-nunito text-green-800">Nuxt Finance</p>
        </header>
        <div class="px-4 grow">
            <div class="grid gap-2">
               <NuxtLink
               :href="item.path" 
               v-for='(item, index) in items' 
               :key='index'
               class="flex items-center gap-2 px-2 py-1 transition rounded cursor-pointer hover:bg-neutral-100"
               >
               <Icon size="20" :name='item.icon' style="color:black"/>
                <span>{{ item.title }}</span>
               </NuxtLink> 
            </div>
        </div>
    </div>
</template>

