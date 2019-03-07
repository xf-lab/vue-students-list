<template>
    <div class="col-xs-12 col-sm-6">
        <h2>Student: {{ name }}</h2>
        <h5>Mark: {{ mark }}</h5>
        <h6>Id: {{ id }}</h6>
        <div class="input-group mb-3">
			<div class="input-group-prepend">
		    	<label class="input-group-text" for="inputGroupSelect01">Mark:&nbsp;</label>
			</div>
			<select v-on:change="onChange($event)" class="custom-select" id="inputGroupSelect01" v-model="key">
			    <!-- <option selected>Select Mark...</option>  -->
			    <option v-for="opt in optionMark" v-bind:value="opt">{{ opt }}</option>
			</select>
		</div>
		<button class="btn btn-success btn-lg" @click="saveChanges(key,id)">Save Changes</button>
    </div>

</template>

<script>
export default {
	props: ['mark', 'name', 'id'],
	data: function(){
		return {
			optionMark: [
				"A","B","C","D","F"
			],
			key: ''
		}
	},  
	methods: { 
		onChange(event){
			//console.log(event.target.value);			
		},
		saveChanges(key,id){
			this.mark = key;//Change Mark of the Child
			this.$emit('updateMark',key,id);//Send Updated Mark and id to the parent
		}
	}
}
</script>

<style>

</style>
