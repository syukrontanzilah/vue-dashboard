<script lang="ts" setup>

</script>

<template>
    <div class="grid lg:flex items-start font-nunito">
            <Sidebar/>
        <div class="p-6 lg:px-8 w-full">
            <slot/>            
        </div>
       
    </div>
</template>
