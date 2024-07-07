<script setup>
const props = defineProps(['getNumero1', 'getNumero2','getOperacao','executaOperacao','retornaResposta']);
</script>

<template>
    <form @submit.prevent="props.executaOperacao">
        <div class="row">
            <div class="col-md-1">
                <input @change="props.getNumero1" class="form-control " type="number">
            </div>
            <div class="col-md-2">
                <select @change="props.getOperacao" class="form-control ">
                    <option value="+">Soma (+)</option>
                    <option value="-">Subitração (-)</option>
                    <option value="*">Multiplicação (*)</option>
                    <option value="/">Divisao (/)</option>
                </select>
            </div>
            <div class="col-md-1">
                <input @change="props.getNumero2" class="form-control" type="number">
            </div>
            <div class="col-md-1">
                <button type="submit" class="btn btn-outline-primary">=</button>
            </div>
            <div class="col-1">
                <input class="resultado" type="text" :value="retornaResposta">
            </div>
        </div>
    </form>
</template>