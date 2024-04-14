<script setup>
import { reactive, ref } from 'vue';

const nums1 = ref('')
const nums2 = ref('')

let numero1 = nums1;
let numero2 = nums2;

const estado = reactive({
    operacao: '',
})

function capturaOp(evento) {
    estado.operacao = evento.target.value
}

</script>

<template>
    <div class="container">
        <header class="p-5 mb-4 mt-4 bg-dark rounded-3">
            <h1 class="text-danger text-center">Calculadora</h1>
        </header>
        <form class="form-group">
            <div class="row mb-5">
                <label>Escolha a operação</label>
                <select class="form-control" @change="capturaOp">
                    <option value="">Operações</option>
                    <option value="soma">Soma</option>
                    <option value="subtracao">Subtração</option>
                    <option value="divisao">Divisão</option>
                    <option value="multiplicacao">Multiplicação</option>
                </select>
            </div>
            <div class="row p-5">
                <div class="col-md-6">
                    <label>Número 1</label>
                    <input v-model="nums1" class="form-control" type="number" required placeholder="Digite um número" />
                </div>
                <div class="col-md-6">
                    <label>Número 2</label>
                    <input v-model="nums2" class="form-control" type="number" required placeholder="Digite um número" />
                </div>
            </div>
            <div class="row">
                <h2 class="text-center">Resultado</h2>
                <h3 v-if="estado.operacao === 'soma'" class="text-center mt-4">{{ numero1 +
                    numero2 }} <p class="mt-4">Você está somando</p>
                </h3>
                <h3 v-else-if="estado.operacao === 'subtracao'" class="text-center mt-4">{{
                    numero1 - numero2 }} <p class="mt-4">Você está subtraindo</p>
                </h3>
                <h3 v-else-if="estado.operacao === 'divisao'" class="text-center mt-4">{{
                    numero1 / numero2 }} <p class="mt-4">Você está dividindo</p>
                </h3>
                <h3 v-else class="text-center mt-4">{{ numero1 * numero2 }} <p class="mt-4">
                        Você está multiplicando</p>
                </h3>
            </div>
        </form>
    </div>
</template>