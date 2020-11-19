<template>
<div class="container">
    <button @click="toggleModal">打开Modal对话框</button>
    <transition name="fade">
        <model v-show="showModal" @closeModel="closeModel" @confirmModel="confirmModel" :title="modelTitle" :content="modelContent" />
    </transition>
</div>
</template>

<script>
import Model from '../components/model/model'
export default {
    name: 'index',
    data() {
        return {
            showModal: false,
            modelTitle: '我是一个标题',
            modelContent: '我是正文内容'
        }
    },
    components: {
        Model
    },
    methods: {
        toggleModal: function () {
            this.showModal = !this.showModal;
        },
        closeModel: function () {
            this.showModal = !this.showModal;
            window.alert('您取消了');
        },
        confirmModel() {
            this.showModal = !this.showModal;
            window.alert('您确定了')
        }
    }

}
</script>

<style>
.container {
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}

.title {
    font-family:
        'Quicksand',
        'Source Sans Pro',
        -apple-system,
        BlinkMacSystemFont,
        'Segoe UI',
        Roboto,
        'Helvetica Neue',
        Arial,
        sans-serif;
    display: block;
    font-weight: 300;
    font-size: 100px;
    color: #35495e;
    letter-spacing: 1px;
}

.subtitle {
    font-weight: 300;
    font-size: 42px;
    color: #526488;
    word-spacing: 5px;
    padding-bottom: 15px;
}

.links {
    padding-top: 15px;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
