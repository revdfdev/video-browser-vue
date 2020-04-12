<template>
    <div>
        <input name="test_input" @input="onInput" />
    </div>
</template>


<script>
export default {
    name: 'SearchBar',
    methods: {
        onInput: function (e) {
            this.$emit('termChange', e.target.value);
        }
    }
}
</script>

<style scoped>
    input {
        outline-style: solid;
        width: 75%;
        outline: auto;
        outline-color: #495057;
    }
    
    div {
        text-align: center;
        margin: 20px;
    }
</style>