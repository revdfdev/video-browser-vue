<template>
    <div class="input-group m-3">
        <input name="test_input" class="form-input" @input="onInput" />
        <div class="input-group-append">
        	<button class="btn btn-outline-seconday" @click="onSearchClick">
        		<i class="fa fa-search"></i> Search
        	</button>
        </div>
    </div>
</template>


<script>
export default {
    name: 'SearchBar',
    data: function () {
    	return {
    		searchTerm: ""
    	};
    },
    methods: {
        onInput: function (e) {
            this.searchTerm = e.target.value;
        },
        onSearchClick: function(e) {
        	this.$emit('termChange', this.searchTerm);
        }
    }
}
</script>

<style scoped>
    input {
        width: 75%;
    }
    
    div {
        text-align: center;
    }
</style>