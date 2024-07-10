<template>
  <div class="click" v-if="showBlock" @click="stopTimer">
    click me!!
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return{
            showBlock : false,
            timer: null,
            reactionTimer: 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true,
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTimer +=10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            console.log(this.reactionTimer)
            this.$emit('end', this.reactionTimer)
        }
    }
}
</script>

<style>
.click{
    width: 400px;
    background: #06c99f;
    margin: 40px auto;
    padding: 100px 0;
    border-radius: 10px;
    text-align: center;
    color: white;
}
</style>