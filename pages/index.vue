<script lang="ts" setup>
import {
  Tabs,
  TabsContent,
  TabsList,
  TabsTrigger,
} from '@/components/ui/tabs'
const loading = ref(false)
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
            <!-- <div class="flex items-center gap-4">
                <div 
                v-for="(item, index) in 3" 
                :key="index"
                class="w-[120px] h-[36px] bg-neutral-200"
                ></div>
            </div>
            <section>
                <div class="w-ful h-[360px] bg-neutral-200"></div>
            </section> -->
    <Tabs default-value="account" class="w-full">
    <TabsList class="bg-green-600 text-white">
      <TabsTrigger value="today">
        Today
      </TabsTrigger>
      <TabsTrigger value="week">
        Week
      </TabsTrigger>
      <TabsTrigger value="month">
        Month
      </TabsTrigger>
      <TabsTrigger value="year">
        Year
      </TabsTrigger>
    </TabsList>
    <TabsContent value="today">
        this today tab
    </TabsContent>
    <TabsContent value="week">
        this week tab
    </TabsContent>
    <TabsContent value="month">
        this month tab
    </TabsContent>
    <TabsContent value="year">
        this year tab
    </TabsContent>
  </Tabs>
        </main>
        <footer>
            footer
        </footer>
    </div>
</template>




