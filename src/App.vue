<script setup lang="ts">
import { ref } from 'vue';

interface Operador {
    operador: string;
}

const operadores = ref<Operador[]>([
    {
        operador: 'Adição'
    },
    {
        operador: 'Subtração'
    },
    {
        operador: 'Multiplicação'
    },
    {
        operador: 'Divisão'
    }
]);

const operadorSelecionado = ref<string>('Adição'); 
const numero1 = ref<string>(''); 
const numero2 = ref<string>(''); 
const resultado = ref<string | number>(''); 

const calcular = () => {
    const num1 = parseFloat(numero1.value);
    const num2 = parseFloat(numero2.value);

    switch (operadorSelecionado.value) {
        case 'Adição':
            resultado.value = num1 + num2;
            break;
        case 'Subtração':
            resultado.value = num1 - num2;
            break;
        case 'Multiplicação':
            resultado.value = num1 * num2;
            break;
        case 'Divisão':
            resultado.value = num1 / num2;
            break;
    }
}
</script>

<template>
    <div class="container">
        <form>
            <h1>Calculadora simples</h1>
            <div class="row">
                <div class="col">
                    <div class="form-group mb-5">
                        <select v-model="operadorSelecionado" class="form-control" id="exampleSelect1">
                            <option v-for="operador in operadores" :value="operador.operador">
                                {{ operador.operador }}
                            </option>
                        </select>
                    </div>
                </div>
                <div class="col">
                    <div class="form-group mb-2">
                        <input type="number" v-model="numero1" class="form-control" id="exampleInput1"
                            placeholder="Digite o primeiro número" @blur="calcular">
                    </div>
                </div>
                <div class="col">
                    <div class="form-group mb-2">
                        <input type="number" v-model="numero2" class="form-control" id="exampleInput2"
                            placeholder="Digite o segundo número" @blur="calcular">
                    </div>
                </div>
            </div>
            <p>Resultado: {{ resultado }}</p>
        </form>
    </div>
</template>

<style scoped></style>
