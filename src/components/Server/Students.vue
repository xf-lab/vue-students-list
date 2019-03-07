<template>
    <div class="col-xs-12 col-sm-6">
        <ul class="list-group">
            <li class="list-group-item"
                    v-for="(listItem, index) in list">
                {{ listItem.name }} - {{ listItem.mark }} {{ mark }} <button class="btn btn-primary btn-sm" @click="editStudent(index)">Edit Mark</button>
            </li>
        </ul>
    </div>
</template>
<style scoped>
.btn-sm{
	position:absolute;
	top: 9px;
	right: 20px;
}
</style>
<script>
export default {
	props: ['list'],
	data: function(){
		return {
			
		}
	},
	methods: { 
		editStudent(id){
			this.$emit('sendMark',this.list[id].mark);
			this.$emit('sendName',this.list[id].name);
			this.$emit('sendId',id);
			//this.$emit('sendObj',this.list);

		}
	}
}
</script>