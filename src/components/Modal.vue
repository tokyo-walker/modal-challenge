<template>
    <div>
        <div class="checkbox-pink">
            <input type="checkbox" id="pink-modal-sign" value="pink" v-model="checkedModalNames">
            <label for="pink-modal-sign">pink</label>
        </div>
        <div class="checkbox-blue">
            <input type="checkbox" id="blue-modal-sign" value="blue" v-model="checkedModalNames">
            <label for="blue-modal-sign">bleu</label>
        </div>
        <div class="checkbox-green">
            <input type="checkbox" id="green-modal-sign" value="green" v-model="checkedModalNames">
            <label for="green-modal-sign">green</label>
        </div>
        <button @click="show">show modal</button>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                title: "Header",
                text: "Hello Vue.js!"
            }
        }
    }
</script>

<style scoped>
    .checkbox-pink {
        font-size: 20px;
        font-weight: bold;
        color: #ff1493;
    }

    .checkbox-blue {
        font-size: 20px;
        font-weight: bold;
        color: #87cefa;
    }

    .checkbox-green {
        font-size: 20px;
        font-weight: bold;
        color: #32cd32;
    }
</style>