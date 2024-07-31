<script lang="ts" setup>
import { useRoute } from 'vue-router'
const route = useRoute()

const items = ref([
    { title: "Overview", path:'/', icon:'tabler:layout-dashboard-filled'},
    { title: "Transactions", path:'/transactions', icon:'icon-park-solid:transaction'},
    { title: "Account", path:'/account', icon:'material-symbols:account-circle'},
    { title: "Contacts", path:'/contacts', icon:'mage:contact-book-fill'},
    { title: "Settings", path:'/settings', icon:'icon-park-solid:setting-two'},
])
import { ref } from 'vue';
const active = ref('active');
const inactive = ref('inactive')
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
               :class="`flex items-center gap-2 px-2 py-1 transition rounded cursor-pointer hover:bg-neutral-100 my-class-${route.path === item.path? active : inactive} transition`"
               >
               <Icon size="20" :name='item.icon' style="color:black"/>
                <span>{{ item.title }}</span>
               </NuxtLink> 
            </div>
        </div>
    </div>
</template>

<style>
.my-class-active {
  background-color: rgb(136, 192, 160);
  font-weight: 700;
  &:hover{
  background-color: rgb(136, 192, 160);
  }
}
.my-class-inactive {
  color: black;
}
</style>

