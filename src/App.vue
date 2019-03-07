<template>
    <div class="container">
        <app-header></app-header>
        <hr>
        <div class="row">
            <students 
                :list="list" 
                @sendMark= "markStudent = $event" 
                @sendName= "nameStudent = $event" 
                @sendId= "id = $event">
                
            </students>
            <app-student-details 
                :mark="markStudent" 
                :name="nameStudent"
                :id="id"
                @updateMark="update">
                    
            </app-student-details>
        </div>
        <hr>
        <app-footer></app-footer>
    </div>
</template>

<script>
    import Header from './components/Shared/Header.vue';
    import Footer from './components/Shared/Footer.vue';
    import Students from './components/Server/Students.vue';
    import StudentDetails from './components/Server/StudentDetails.vue';

    export default {
        data: function(){
            return {
                markStudent: '',
                nameStudent: '',
                id: 0,
                list: [
                    {name:'John', mark:''},
                    {name:'Frank', mark:''},
                    {name:'Axel', mark:''},
                    {name:'Bob', mark:''},
                    {name:'Max', mark:''}
                ],
            };
        },
        methods: {
            update(key,id) {
                this.list[id].mark = key;
                console.log(key);
            }
        },
        components: {
            appHeader: Header,
            Students,
            'app-student-details': StudentDetails,
            'app-footer': Footer
        }
    }
</script>

<style>

</style>
