<template>
  <h2>Admin Dashboard</h2>
  <!-- open modal -->
  <div v-if="showModal">
    <!-- used component -->
    <ModalComponent :header="successHeader" :content="successContent" :theme="successTheme" @hideModal="showModal = false" />
  </div>

  <!-- close modal -->
  <div v-if="deleteModal">
    <!-- used component -->
    <ModalComponent :header="dangerHeader" :content="dangerContent" :theme="deleteTheme" @hideModal="deleteModal = false">
      <!-- creat a slot -->
      <h2>Login Success!</h2>
      <p>Welcome user name</p>
    </ModalComponent>
  </div>
  <button @click="showModal = true">Open</button><br>
  <button @click="deleteModal = true">Delete</button>
</template>

<script>
// defined component
import ModalComponent from './components/ModalComponent.vue'

export default {
  data() {
    return {
      successHeader: 'Login Success!',
      successContent: 'Welcome',
      dangerHeader: 'Are you sure want to delete?',
      dangerContent: 'We are so sorry to hear from you!',
      successTheme: 'success',
      deleteTheme: 'danger',
      showModal: false,
      deleteModal: false
    }
  },
  methods: {
    
  },
  // registraction component
  components: {
    ModalComponent
  }
}
</script>

<style>

</style>