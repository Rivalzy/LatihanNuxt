<template>
  <div>
    <button @click="msg = 'Hello'">Ubah Pesan</button>
    <p>{{ msg }}</p>
  </div>
</template>

<script>
export default {
  layout(context) {
    return 'custom'
  },
  data() {
    return { msg: '' }
  },

  created() {
    this.msg = 'Hello'
  },

  beforeMount() {
    this.msg = 'Hello World'
  },

  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start()
      setTimeout(() => {
        this.$nuxt.$loading.finish()
      }, 5000)
    })
  },

  beforeUpdate() {
    this.msg = 'Hello World again'
  },
}
</script>
