<template>
  <div class="progress-bar">
      <span style="position: absolute; height: 10px;">{{ Math.round(porcentagemConcluida) + '%' }}</span>
      <div class="completed" :style="{width:porcentagemConcluida + '%'}"></div>
  </div>    
</template>

<script>
export default {
    name: "ProgressBar",
    props: {
        values: {
            required: true,
            type: Array
        }
    },
    computed: {
        porcentagemConcluida() {
            const completedItens = this.values.filter(value => value.completed == true)
            return this.values.length != 0 ? (completedItens.length * 100) / this.values.length : 0;
        }
    }
}
</script>

<style>
    .progress-bar {
        display: flex;
        justify-content: center;
        border: 0.5px solid black;
        border-radius: 10px;
        height: 30px;
        width: 800px;
    }

    .completed {
        background-color: green;
        border-radius: 10px;
    }
</style>