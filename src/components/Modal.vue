<template>
    <div class="checkbox-pink">
        hoge
        <input type="checkbox" id="modal-sign" value="pink" v-model="checkbox">
        <label for="modal-sign">pink</label>
    </div>
</template>

<script lang="ts">
    import {ref, reactive, defineComponent} from 'vue'


    export default defineComponent({
        name: 'ModalComponent',
        props: {
            msg: {
                type: String,
                required: true,
            },
        },
        setup: () => {
            let checkbox = reactive([])

            return {checkbox}
        },
    })
</script>