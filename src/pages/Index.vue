<template>
    <div>
        <div style="color: #ff1493; font-size: 20px; font-weight: bold">
            <input type="checkbox" id="pink-modal-sign" value="pink" v-model="checkedModalNames">
            <label for="pink-modal-sign">pink</label>
        </div>
        <div style="color: #87cefa; font-size: 20px; font-weight: bold">
            <input type="checkbox" id="blue-modal-sign" value="blue" v-model="checkedModalNames">
            <label for="blue-modal-sign">bleu</label>
        </div>
        <div style="color: #32cd32; font-size: 20px; font-weight: bold">
            <input type="checkbox" id="green-modal-sign" value="green" v-model="checkedModalNames">
            <label for="green-modal-sign">green</label>
        </div>
        <button @click="show">show modal</button>
    </div>
    <div v-if="modal" id="overlay">

        <div v-if="modalPink" id="pink-modal" class="modal-container" @click.self="closePinkModal">
            <div class="modal-pink-body">
                <p>Hello world</p>
                <div class="modal-footer">
                    <button @click="closePinkModal">閉じる</button>
                </div>
            </div>
        </div>

        <div v-if="modalBlue" id="blue-modal" class="modal-container" @click.self="closeBlueModal">
            <div class="modal-blue-body">
                <p>Hello world</p>
                <div class="modal-footer">
                    <button @click="closeBlueModal">閉じる</button>
                </div>
            </div>
        </div>

        <div v-if="modalGreen" id="green-modal" class="modal-container" @click.self="closeGreenModal">
            <div class="modal-green-body">
                <p>Hello world</p>
                <div class="modal-footer">
                    <button @click="closeGreenModal">閉じる</button>
                </div>
            </div>
        </div>

    </div>
</template>
<script lang="ts">
    import {defineComponent} from 'vue'

    export default defineComponent({
        name: 'App',
        components: {},
        data() {
            return {
                modal: false,
                modalPink: false,
                modalBlue: false,
                modalGreen: false,
                checkedModalNames: [],
            }
        },
        // composition API
        setup() {
        },
        methods: {
            show(): void {
                this.modal = true;
                for (let modalName of this.checkedModalNames) {
                    switch (modalName) {
                        case 'pink':
                            this.modalPink = true;
                            break;
                        case 'green':
                            this.modalGreen = true;
                            break;
                        case 'blue':
                            this.modalBlue = true;
                            break;
                    }
                }
            },
            close(): void {
                this.modal = false;
            },
            closePinkModal(): void {
                this.modalPink = false;
                if (!this.modalBlue && !this.modalGreen) {
                    this.initializeIndexPage();
                }
            },
            closeBlueModal(): void {
                this.modalBlue = false;
                if (!this.modalGreen) {
                    this.initializeIndexPage();
                }
            },
            closeGreenModal(): void {
                this.modalGreen = false;
                this.initializeIndexPage();
            },
            initializeIndexPage(): void{
                this.modal = false;
                this.checkedModalNames = [];
            },
        },
    })
</script>
<style>
    #overlay {
        z-index: 1;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.5);
        display: flex;
        align-items: center;
        justify-content: center;
    }

    #pink-modal {
        z-index: 30;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    #blue-modal {
        z-index: 20;
        position: fixed;
        top: 0;
        left: 0;
        width: 90%;
        height: 90%;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    #green-modal {
        z-index: 10;
        position: fixed;
        top: 0;
        left: 0;
        width: 80%;
        height: 80%;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .modal-pink-body {
        background-color: white;
        border-radius: 4px;
        width: 30%;
        height: 20%;
        border: 1px solid #ff1493;
        color: #ff1493;
    }

    .modal-blue-body {
        background-color: white;
        border-radius: 4px;
        width: 30%;
        height: 20%;
        border: 1px solid #87cefa;
        color: #87cefa;
    }

    .modal-green-body {
        background-color: white;
        border-radius: 4px;
        width: 30%;
        height: 20%;
        border: 1px solid #32cd32;
        color: #32cd32;
    }
</style>