<template>
  <div :class="[tarefa.completed ? 'tarefa-concluida' : 'tarefa-open', 'tarefa']">
      <span @click="$emit('concluirTarefa', tarefa)"><strong>{{ tarefa.name }}</strong></span>
      <button class="excluir-button" @click="$emit('excluirTarefa', tarefa)">X</button>
  </div>    
</template>

<script>
export default {
    name:"Tarefa",
    props: {
        tarefa: {
            required: true,
            type: Object
        }
    }
}
</script>

<style>
    .tarefa {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 200px;
        height: 100px;
        margin: 20px;
    }

    .tarefa-open {
        background-color: #e80505;
        border-radius: 10px;
        border-left: 10px solid #a80000;
    }

    .tarefa-concluida {
        background-color: #008f07;
        border-radius: 10px;
        border-left: 10px solid #016b06;
    }
    
    .tarefa-concluida span {
        text-decoration: line-through;
    }

    .excluir-button {
        position: relative;
        color: white;
        bottom: 35%;
        background-color: rgba(0, 0, 0, 0.35);
        border-radius: 50%;
        border: none;
    }

    span {
        width: 80%;
        height: 20%;
        text-align: center;
    }
</style>