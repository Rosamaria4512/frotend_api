<template>
  <div class="about container">
    <post-component />
    <hr>
    <get-component />
    <hr>
    <put-component />
    
  </div>
</template>

<script>
import PostComponent from '@/components/PostComponent.vue'
import GetComponent from '../components/GetComponent.vue'
import PutComponent from '../components/PutComponent.vue'

export default {
  name: 'AboutView',
  components: {
    GetComponent,
    PostComponent,
    PutComponent,
    
  }
}
</script>
