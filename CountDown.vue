<template>
  <div>
    <span class="text">{{hour}}</span><span>:</span><span class="text">{{minute}}</span><span>:</span><span class="text">{{second}}</span>
  </div>
</template>

<script>
  export default {
    props: {
      date: {
        default: new Date().getTime() + (3 * 60 * 60 * 1000)
      }
    },
    data () {
      return {
        hour: '00',
        minute: '00',
        second: '00',
        count: this.date - new Date().getTime()
      }
    },
    created () {
      this.start()
    },
    methods: {
      start () {
        setInterval(() => {
          this.count = this.count - 1000

          this.hour = parseInt(this.count / (60 * 60 * 1000)) + ''
          if (this.hour < 10) {
            this.hour = '0' + this.hour
          }
          let n = this.count % (60 * 60 * 1000)
          this.minute = parseInt(n / (60 * 1000)) + ''
          if (this.minute < 10) {
            this.minute = '0' + this.minute
          }
          let n2 = n % (60 * 1000)
          this.second = parseInt(n2 / 1000) + ''
          if (this.second < 10) {
            this.second = '0' + this.second
          }
        }, 1000)
      }
    },
    computed: {}
  }
</script>

<style scoped>
  .text{
    background-color: #000000;
    color: #ffffff;
    padding: 3px 2px;
    border-radius: 2px;
  }
</style>
