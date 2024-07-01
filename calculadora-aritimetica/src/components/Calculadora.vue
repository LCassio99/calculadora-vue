<template>
    <div class="calculator">
        <input type="number" v-model.number="number1" @input="calculate" placeholder="Primeiro número">
        <select v-model="operation" @change="calculate">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
        </select>
        <input type="number" v-model.number="number2" @input="calculate" placeholder="Segundo número">
        <div class="result">
            <h3>Resultado: {{ result.toFixed(3) }}</h3>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            number1: 0,
            number2: 0,
            operation: '+',
            result: 0
        };
    },
    methods: {
        calculate() {
            switch (this.operation) {
                case '+':
                    this.result = this.number1 + this.number2;
                    break;
                case '-':
                    this.result = this.number1 - this.number2;
                    break;
                case '*':
                    this.result = this.number1 * this.number2;
                    break;
                case '/':
                    this.result = this.number2 !== 0 ? this.number1 / this.number2 : 'Não pode ser dividido por 0';
                    break;
            }
        }
    },
    mounted() {
        this.calculate();
    }
};
</script>

<style scoped>
.calculator {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 50px;
}

input,
select {
    margin: 10px;
    padding: 10px;
    font-size: 1.2em;
}

.result {
    margin-top: 20px;
}
</style>