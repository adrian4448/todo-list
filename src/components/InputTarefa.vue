<template>
  <div class="input-tarefa">
      <input type="text" v-model="tarefa.name">
      <button @click="$emit('adicionarTarefa', tarefa)">+</button>
  </div>    
</template>

<script>
export default {
    name:"InputTarefa",
    data() {
        return {
            tarefa: {
                name: '',
                completed: false
            }
        }
    }
}
</script>

<style>
    .input-tarefa {
        margin: 20px;    
    }

    .input-tarefa input {
        background-color: rgba(0,0 ,0 ,0.30);
        color: white;
        border: none;
        width: 300px;
        height: 30px;
        border-radius: 2px;
    }

    .input-tarefa button {
        position: relative;
        right: 30px;
        width: 30px;
        height: 32px;
        background-color: #00b6c7;
        border: none;
        color: white;
        border-end-end-radius: 2px;
        border-start-end-radius: 2px;
    }

    .input-tarefa button:hover {
        background-color: #00a3b3;
    }
</style>