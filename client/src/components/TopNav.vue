<script lang="ts" setup>
let props=defineProps<{
    data:{
        res:any,
        note: string,
        parsedUserDetails:{
            username:string
        },
        screenWidth:any,
    }
}>()

function clearChats(){
    localStorage.removeItem("chats")
    window.location.reload()
}
</script>
<template>
    <div class="h-[44px] bg-white z-5 fixed top-0 right-0 border-b-[1px]" :style="props.data.screenWidth>720?'left:300px':'left:0;'">
        <div class="flex px-5 py-3 items-center justify-between w-full">
            <p v-if="props.data.parsedUserDetails.username!==undefined" class="text-black text-sm font-semibold">{{props.data.parsedUserDetails.username}}</p>
            <p v-else class="text-black text-sm font-semibold">Gemmie</p>
            <button  v-if="props.data.screenWidth<720&&props.data.res.length>0" class="text-sm text-blue-500 active:underline" @click="clearChats">Clear chats</button>
        </div>
        <div class="bg-blue-200 flex items-center justify-center text-xs h-[20px]">
            <p>{{ props.data.note }}</p>
        </div>
    </div>
</template>
