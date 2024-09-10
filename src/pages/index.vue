<template>
  
   <!-- <Login /> -->

  
   

</template>

<script setup>

 import { ref } from 'vue' 
 import { netsh } from 'vue'
 import { ssh } from 'vue'


  const ip = ref()
  const port = ref()
  const connected = ref()
  
function getIp(ip, port){
  computed(() => {
     connected.value = netsh.ip
    
    
  })
  
}
  
  

</script>
