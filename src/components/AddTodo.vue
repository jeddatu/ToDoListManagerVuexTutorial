<template>
    <div>
        <form @submit="onSubmit">
            <input type="text" v-model="title" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script lang="ts">
import { mapActions } from'vuex';
import uuid from 'uuid';
import Vue from 'vue'

export default Vue.extend({
    name: 'AddTodo',
    data() {
        return {
            title: '',
        }
    },
    methods: {
        ...mapActions(['addTodo']),
        onSubmit(e) {
            e.preventDefault();
            this.addTodo(this.title);
            this.title = '';
        }
    }
})
</script>

<style scoped>
    form {
        display: flex;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
        border: 1px solid #41b883;
        outline: 0;
    }

    input[type="submit"] {
        flex: 2;
        background: #41b883;
        color: #fff;
        border: 1px #41b883 solid;
        cursor: pointer;
    }
</style>
