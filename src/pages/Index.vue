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
    <div v-if="visibleModal" class="overlay">

        <div v-if="visibleModalPink" id="pink-modal" class="pink-modal-body" @click.self="closePinkModal">
            <div class="modal-pink-body">
                <p>Hello world</p>
                <div class="modal-footer">
                    <button @click="closePinkModal">閉じる</button>
                </div>
            </div>
        </div>

        <div v-if="visibleModalBlue" id="blue-modal" class="blue-modal-body" @click.self="closeBlueModal">
            <div class="modal-blue-body">
                <p>Hello world</p>
                <div class="modal-footer">
                    <button @click="closeBlueModal">閉じる</button>
                </div>
            </div>
        </div>

        <div v-if="visibleModalGreen" id="green-modal" class="green-modal-body" @click.self="closeGreenModal">
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
    import { ref, reactive, defineComponent } from 'vue'

    export default defineComponent({
        name: 'App',
        components: {},
        data() {},
        // composition API
        setup() {
            console.log('This is Vue3')
            let visibleModal = ref(false);
            let visibleModalPink = ref(false);
            let visibleModalBlue = ref(false);
            let visibleModalGreen = ref(false);
            let checkedModalNames = ref([]);

            return {
                visibleModal,
                visibleModalPink,
                visibleModalBlue,
                visibleModalGreen,
                checkedModalNames,
            }
        },
        methods: {
            show(): void {
                this.visibleModal = true;
                for (let modalName of this.checkedModalNames) {
                    switch (modalName) {
                        case 'pink':
                            this.visibleModalPink = true;
                            break;
                        case 'green':
                            this.visibleModalGreen = true;
                            break;
                        case 'blue':
                            this.visibleModalBlue = true;
                            break;
                    }
                }
            },
            close(): void {
                this.visibleModal = false;
            },
            closePinkModal(): void {
                this.visibleModalPink = false;
                if (!this.visibleModalBlue && !this.visibleModalGreen) {
                    this.initializeIndexPage();
                }
            },
            closeBlueModal(): void {
                this.visibleModalBlue = false;
                if (!this.visibleModalGreen) {
                    this.initializeIndexPage();
                }
            },
            closeGreenModal(): void {
                this.visibleModalGreen = false;
                this.initializeIndexPage();
            },
            initializeIndexPage(): void {
                this.visibleModal = false;
                this.checkedModalNames = [];
            },
        },
    })
</script>
<style>
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

    .overlay {
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

    .pink-modal-body {
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

    .blue-modal-body {
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

    .green-modal-body {
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