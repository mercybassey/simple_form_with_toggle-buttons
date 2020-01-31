<template>
     <div id="app">
        <div class="container">
            <div class="row">
                <div class="col-md-6">
                        <table class="table border">
                                <thead>
                                <tr>
                                    <th scope="col">id</th>
                                    <th scope="col">name</th>
                                    <th scope="col">role</th>
                                   
                                    <th scope="col">Score</th>
                                    <th scope="col">email</th>
                                
                                </tr>
                                </thead>
                                <tbody>
                                <tr v-for ="(person,index) in persons">
                                        <th scope="row">{{parseInt(index) +1}}</th>
                                        <td>{{person.name}}</td>
                                        <td>{{person.role}}</td>
                                        <td> {{person.score}}</td>
                                        <td> {{person.email}}</td>
                                        

                                        <td>
                                            <button class="btn btn-danger" @click="removeItem(index)">delete</button>
                                            <button class="btn btn-info" @click="updateItem(person)">edit</button>
                                        </td>
                                </tr>
                                
                                    
                                </tbody>
                        </table>
                </div>

                <div class="col-md-6">
                    <div class="card shadow p-4">
                        <h2 class="mb-4">Please Add New Users</h2>
                        <p>your name is {{user.name}} and your role is {{user.role}}</p>

                        <form @submit.prevent="addUser">
                                <div class="form-group">
                                    <label>Name</label>
                                    <input v-model="user.name" type="text" id="name" class="form-control">
                                </div>
                                <div class="form-group">
                                        <label>Role</label>
                                        <input v-model="user.role" type="text" id="score" class="form-control">
                                </div>
                                
                                 <div class="form-group">
                                        <label>score</label>
                                        <input v-model="user.score" type="text" id="role" class="form-control">
                                </div>

                                  <div class="form-group">
                                        <label>email</label>
                                        <input v-model="user.email" type="text" id="role" class="form-control">
                                </div>
                                
                                
                                <div class="form-group">
                                        
                                        <button v-if="status" type="submit" class="btn btn-primary" >submit</button>
                                        <button v-else type="click" @click.prevent="updatePerson()" class="btn btn-primary" >update</button>
                                        <button type="reset" id="reset" class="btn btn-danger" @click="addSubmit" ml-4>reset</button>
                                        
                                </div>
                        </form>
                        <p> the total score is {{ getTotalScore}} and the total contacts are {{ getTotalContacts }}</p>
                    </div>
                   
                </div>
                
            </div>
        </div>
    </div>

</template>

<script>
export default {
    data(){
        return{
            
            user: {
                name: "",
                role: "",
                score: "",
                email: "",
                
            },
            status: true,
            
            persons: [
                {name:"mercy", role:"vue js",score:"100",email:"udohmercy911@gmail.com"},
                {name:"wisdom", role:"js dev",score:"50",email:"wizzybobo@gmail.com"},
                {name:"stanley", role:"html dev",score:"40",email:"stan@gmail.com"},
                {name:"ekemini", role:"css dev", score:"50",email:"kemzytony@gmail.com"},
                {name:"dora", role:"vuejs dev" ,score:"30",email:"nyonganniebet@gmail.com"}
            ]
        }

        
    },
    
    methods: {
        addUser(){
           this.persons.push(this.user);
        
        },
        removeItem(index){
            this.persons.splice(index,1);
          
             
        },
        updateItem(id){
            // console.log(id);
            // this.user.name = id.name;
            // this.user.role = id.role;
            this.user = id;
            this.status = !this.status;
            
        },
        updatePerson(index){
            this.persons.push();
        },
        addSubmit(){
            this.status=!this.status;
        }
        // checkStatu{
        //     if(this.status){
        //         console.log("hello");
        //     }else{
        //         console.log("hey");
        //     } 
        // }
    },
    computed: {
        getTotalScore(){
        let total=0;
            for(let i=0; i < this.persons.length; i++){
                total+=parseInt(this.persons[i].score)
            }
            return total;
        },
        getTotalContacts(){
            let totalContacts = 0;
            for(let i=0; i < this.persons.length; i++){
                totalContacts+=parseInt(this.persons[i].index)
            }
        }
        
    }
}
</script>