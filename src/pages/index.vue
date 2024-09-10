<template>
  
   <!-- <Login /> -->

  <input v-model="ip" />
  
   

</template>

<script setup>

 import { ref } from 'vue' 
 import { netsh } from 'vue'
 import { ssh } from 'vue'
 import { axios } from 'axios'


  const ip = ref()
  const port = ref()
  const connected = ref()
  const list = ref([])
  
function getIp(ip, port){
  computed(() => {
     connected.value = netsh.ip
    
    
  })
  
}
function pushData(){
  connected = axios.get(() =>{

    list.value.push({
      
    })
  })
}


</script>
