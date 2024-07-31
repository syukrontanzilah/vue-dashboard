<script lang="ts" setup>
import {
  Tabs,
  TabsContent,
  TabsList,
  TabsTrigger,
} from '@/components/ui/tabs'
import { ref, resolveComponent } from 'vue'
const loading = ref(false)
const TabsToday = resolveComponent('TabsToday')
const TabsWeek = resolveComponent('TabsWeek');
const TabsMonth = resolveComponent('TabsMonth');
const TabsYear = resolveComponent('TabsYear')
const list = [
    {title: "today", component: TabsToday},
    {title: "week", component:TabsWeek},
    {title: "month", component:TabsMonth},
    {title: "year", component:TabsYear},
]
</script>

<template>
    <div class="grid gap-4 w-full">
        <header class="flex items-start justify-between">
            <div class="grow">
             <h1>Dashboard</h1>
            <p>Hi, Welcome back to Dashboard!</p>               
            </div>
            <div class="w-[120px] h-[36px] bg-neutral-200"></div>

        </header>
        <main class="grid gap-4">
    <Tabs default-value="today" class="w-full">
    <TabsList class="bg-green-600 text-white">
      <TabsTrigger 
      v-for="item, index in list" 
      :value="item.title"
      :key="index"
      >
        {{item.title}}
      </TabsTrigger>
    </TabsList>
    <TabsContent 
    v-for="item, index in list" 
    :value="item.title"
    :key="index"
    >
    <!-- {{ item.component }} -->
    <component :is="item.component" />
    </TabsContent>
  </Tabs>
        </main>
        <footer>
            <!-- footer -->
        </footer>
    </div>
</template>




