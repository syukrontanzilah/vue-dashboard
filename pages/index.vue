<script lang="ts" setup>
import { useHead } from '@vueuse/head'
useHead({
  title: 'Overview'
})
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
];
let data = ref([16.0, 18.2, 23.1, 27.9, 32.2, 36.4, 39.8, 38.4, 35.5, 29.2, 22.0, 17.8 ])
let categories = ref({
    'today': [],
    'week': [],
    'month': [],
    'year':[]
})

let currentCategory = ref(['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep','Oct', 'Nov', 'Dec'])

const options = computed(()=>({
    chart: {
        type: 'line',
        animation: {
            // enabled: false,
        }
    },
    title: {
        text: ''
    },
    legend:{
        enabled: false
    },
    // subtitle: {
    //     text: ''
    // },
    xAxis: {
        gridLineColor:'transparent',
        categories: currentCategory
    },
    yAxis: {
        gridLineColor:'transparent',
        title: {
            text: ''
        }
    },
    plotOptions: {
        line: {
            marker: {
                enable: false
            },
            dataLabels: {
                enabled: false
            },
            enableMouseTracking: false
        }
    },
    series: [{
        name: 'line',
        lineWidth:'4px',
        color: {
            linearGradient: {},
            stops:[
               [0,'rgba(252,176,69,1)'],
               [0.33,'rgba(253,29,29,1)'],
               [0.66,'rgba(131,58,180,1)'],
               [1,'rgba(29,217,83,1'],
                
            ]
        },
        data: data.value
    }]
}))

function generateRandomData(){
    
}

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
    <TabsList class="">
      <TabsTrigger 
      v-for="item, index in list" 
      :value="item.title"
      :key="index"
      class="capitalize"
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
    <!-- <component :is="item.component" /> -->
    <highchart :options="options" />

  </TabsContent>
  </Tabs>
        </main>
        <footer>
            <!-- footer -->
        </footer>
    </div>
</template>




