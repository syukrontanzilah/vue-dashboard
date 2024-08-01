<script setup>
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
    today: ['01.00','02.00','03.00'],
    week: ['Sunday', 'Moday', 'Tuesday','Wednesday','Thursday','Friday','Saturday'],
    month: ['Jan', 'Feb','Mar','Apr','Mei','Jun','Jul','Ags','Sep','Oct','Nov','Dec'],
    year:['2021','2022','2023','2024']
})

let currentCategory = ref('today')

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
        categories: categories.value[currentCategory.value]
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

const setCategory = (e) => {
    let v = e.target.innerText.toLowerCase();
    currentCategory.value = v;
    switch(v){
        case 'today':
            generateRandomData(24);
        case 'week':
            generateRandomData(7);
        case 'month':
            generateRandomData(12);
        case 'year':
            generateRandomData(365);
        default:
            generateRandomData(7);

    }
}

function generateRandomData(number=7){
    let values = [];
    for (let i = 0; i < number; i++){
        values.push(Math.floor(Math.random()*100))
    }
    console.log('values', values);
    data.value = values;
    return values;
}

onMounted(()=>{
    generateRandomData()
})

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
    <Tabs default-value="today" @click="setCategory" class="w-full">
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




