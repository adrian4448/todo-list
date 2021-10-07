<template>
	<div id="app">
		<h1>Tarefas</h1>
		<ProgressBar :values="tarefas"/>
		<InputTarefa @adicionarTarefa="adicionarTarefa"/>	
		<div class="tarefas">
			<Tarefa v-for="tarefa in tarefas" :key="tarefa" :tarefa="tarefa" 
					@concluirTarefa="concluirTarefa" @excluirTarefa="excluirTarefa"></Tarefa>	
		</div>
	</div>
</template>

<script>
import Tarefa from './components/Tarefa.vue'
import InputTarefa from './components/InputTarefa.vue'
import ProgressBar from './components/ProgressBar.vue'

export default {
	name: 'App',
	components: { Tarefa, InputTarefa, ProgressBar },
	data() {
		return {
			tarefas: []
		}
	},
	methods: {
		concluirTarefa(tarefa) {
			tarefa.completed = !tarefa.completed;
		},
		excluirTarefa(tarefa) {
			this.tarefas.splice(this.tarefas.indexOf(tarefa), 1)
		},
		adicionarTarefa(tarefa) {
			const newTarefa = Object.assign({}, tarefa);
			this.tarefas.push(newTarefa);
		}
	},
	watch: {
		tarefas: {
			deep: true,
			handler() {
				localStorage.setItem('tarefas', JSON.stringify(this.tarefas));
			}
		}
	},
	created() {
		const json = localStorage.getItem('tarefas');
		this.tarefas = JSON.parse(json) || []
	}
}
</script>

<style>
	body {
		font-family: 'Lato', sans-serif;
		background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
		color: #FFF;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 300;
		font-size: 3rem;
	}

	.tarefas {
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		margin: 20px;
		width: 800px;
	}
</style>
