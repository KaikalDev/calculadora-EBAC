<script setup>
const props = defineProps(['getNumero1', 'getNumero2', 'getOperacao', 'executaOperacao', 'retornaResposta']);

const handleNumero1Change = (event) => {
    props.getNumero1(event);
    props.executaOperacao();
};

const handleNumero2Change = (event) => {
    props.getNumero2(event);
    props.executaOperacao();
};

const handleOperacaoChange = (event) => {
    props.getOperacao(event);
    props.executaOperacao();
};
</script>

<template>
    <form @submit.prevent="props.executaOperacao">
        <div class="row">
            <div class="col-md-1">
                <input @input="handleNumero1Change" class="form-control" type="number">
            </div>
            <div class="col-md-2">
                <select @input="handleOperacaoChange" class="form-control">
                    <option value="+">Soma (+)</option>
                    <option value="-">Subtração (-)</option>
                    <option value="*">Multiplicação (*)</option>
                    <option value="/">Divisão (/)</option>
                </select>
            </div>
            <div class="col-md-1">
                <input @input="handleNumero2Change" class="form-control" type="number">
            </div>
            <div class="col-md-1">
                <button type="submit" class="btn btn-outline-primary">=</button>
            </div>
            <div class="col-1">
                <input class="resultado" type="text" :value="props.retornaResposta">
            </div>
        </div>
    </form>
</template>
