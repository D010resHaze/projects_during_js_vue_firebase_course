<template>
  <div class="backdrop" @click.self="hideModal">
    <div class="modal" :class="{successColor: theme === 'success', dangerColor: theme === 'danger'}">
      <h2>{{ header }}</h2>
      <p>{{ content }}</p>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    hideModal() {
      this.$emit('hideModal');
    }
  },
  props: ['header', 'content', 'theme']
}
</script>

<style>
  .backdrop {
    position: fixed;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgb(134, 134, 134);
  }
  .modal {
    width: 400px;
    margin: 40px auto;
    padding: 30px;
    background-color: white;
  }
  .successColor {
    background-color: green;
    color: white;
  }
  .dangerColor {
    background-color: crimson;
    color: white;
  }
</style>