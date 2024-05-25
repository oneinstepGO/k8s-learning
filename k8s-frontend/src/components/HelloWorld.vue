<template>
  <div class="hello">
    <h1>{{ message }}</h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      message: ''
    };
  },
  mounted() {
    fetch('/api')
        .then(response => response.text())
        .then(data => {
          this.message = data;
        });
  }
};
</script>

<style scoped>
h1 {
  font-size: 2em;
}
</style>