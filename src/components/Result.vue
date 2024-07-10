<template>
  <p>the result is {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: [ "score" ],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if(this.score < 400){
            this.rank = "wave fingers"
        } else if(this.score < 600){
            this.rank = "rapid flex .."
        } else {
            this.rank = "snail pace..."
        }
    }
}
</script>

<style>
.rank{
    font-size: 1.5rem;
    color: #06c99f;
    font-weight: bold;
}
</style>