<template>
    <div>
        <br>
        <br>
        <br>
        <h1>Detail Employee</h1>
        <table>
            <tr>
                <td>Email</td>
                <td>{{email}}</td>
            </tr>
            <tr>
                <td>First Name</td>
                <td>{{first_name}}</td>
            </tr>
            <tr>
                <td>Last Name</td>
                <td>{{last_name}}</td>
            </tr>
            <tr>
                <td>Avatar</td>
                <td><img v-bind:src="avatar"></td>
            </tr>
        </table>
        <br>
        <div style="text-align:center"><Button class="button btnFloat btnBlueGreen"  v-on:click="save">Save to Favorite</Button></div>
    </div>    
</template>
<script>
import Vue from 'vue';
import axios from 'axios'
import VueAxios from 'vue-axios'


Vue.use(VueAxios,axios)


export default {
    name: "DetailEmployee",
    data(){
        return {
            list2:undefined,
            id: this.$route.params.id,
            email: null,
            first_name: null,
            last_name: null,
            avatar: null,
                
        }
        
    },
    methods:{
        save(){

            let list_data = JSON.parse(localStorage.getItem('list_data'));
            let id_data;

            if (localStorage.list_data && localStorage.id_data) {
                list_data = JSON.parse(localStorage.getItem('list_data'));
                id_data = parseInt(localStorage.getItem('id_data'));
            }
            else {
                list_data = [];
                id_data = 0;
            }

            id_data++;
            list_data.push({ 'id_data': id_data, 'email': this.email, 'first_name': this.first_name, 'last_name': this.last_name, 'avatar': this.avatar });
            localStorage.setItem('list_data', JSON.stringify(list_data));
            localStorage.setItem('id_data', id_data);

            alert('Success save Favorite user to local storage')
            
            // let user;    
            // user = JSON.parse(localStorage.getItem('userFavorite'));

            // for(i in user){
            //     console.log("andreas");
            // }

          
            // if(user === null){
            // //    storage = [];
            // }else{
            //     this.queue = JSON.parse(localStorage.getItem('userFavorite'));
            // }

            // this.purchase.email = this.email;
            // this.purchase.first_name = this.first_name;
            // this.purchase.last_name = this.last_name;
            // this.purchase.avatar = this.avatar;

            // this.queue.push(this.purchase);

            // let myObj = {
            //     email: this.email,
            //     first_name: this.first_name,
            //     last_name: this.last_name,
            //     avatar: this.avatar
            // }
            // let myObj_serialized = JSON.stringify(myObj);
            
            // this.storage.push(
            //     {
            //         email: "asd",
            //         first_name: "asd",
            //         last_name: "asd",
            //         avatar: "asd"
            //     }
            // );
            
            //localStorage.setItem("userFavorite", myObj_serialized);
            console.log(localStorage.list_data);
        }
    },
    mounted(){
        Vue.axios.get('https://reqres.in/api/users/'+this.id)
        .then((response)=>{
            this.list2 = response.data
            this.email = this.list2.data.email
            this.first_name = this.list2.data.first_name
            this.last_name = this.list2.data.last_name
            this.avatar = this.list2.data.avatar
        })
    }
    
}
</script>

<style >
    .btnBlueGreen {
  background: #00AE68;
}
</style>