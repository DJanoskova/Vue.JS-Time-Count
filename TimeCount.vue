<template>
  <div class="time-count">
    {{ timeDifference.hours }} hours, {{ timeDifference.minutes }} minutes and {{ timeDifference.seconds }} seconds
  </div>
</template>

<script>
import moment from 'moment'

export default {
  props: ['time'],
  data () {
    return {
      now: moment()
    }
  },
  computed: {
    timeDifference() {
      let seconds, minutes, duration
      duration = moment.duration(this.now.diff(this.time))
      duration = Math.floor(duration.asSeconds())
      seconds = duration % 60
      duration = Math.floor(duration / 60)
      minutes = duration % 60
      duration = Math.floor(duration / 60)
      return {
        seconds,
        minutes,
        hours: duration
      }
    }
  },
  created() {
    setInterval(() => {
      this.now = moment()
    }, 1000)
  }
}
</script>
