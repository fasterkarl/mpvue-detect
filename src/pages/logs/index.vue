<template>
  <div>
    啦啦啦啦啦 {{$route.query}}
    <ul class="container log-list">
      <li v-for="(log, index) in logs"
          :class="{ red: aa }"
          :key="index"
          class="log-item">
        <card :text="(index + 1) + ' . ' + log"></card>
      </li>
    </ul>
  </div>
</template>

<script>
  import { formatTime } from '@/utils/index'
  import card from '@/components/card'

  export default {
    components: {
      card
    },

    data () {
      return {
        logs: []
      }
    },

    created () {
      const logs = (wx.getStorageSync('logs') || [])
      this.logs = logs.map(log => formatTime(new Date(log)))
    },
    mounted () {
      // console.log(this.$root.$mp.query)
      console.log(this.$route.query)
    }
  }
</script>

<style>
  .log-list {
    display: flex;
    flex-direction: column;
    padding: 40rpx;
  }

  .log-item {
    margin: 10rpx;
  }
</style>
