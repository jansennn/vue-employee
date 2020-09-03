<template>
    <div>
        <br>
        <h1>Favorite Employee</h1>
        <div class="card shadow2" v-if="list_data.length === 0">
            <h3>User Favorite masih kosong silahkan Menambahkannya di employee List</h3>
        </div>
        <div class="card shadow2" v-for="item in list_data" v-bind:key="item.id">
            <h2>{{item.first_name}}</h2>
            <pre>Email : {{item.email}}</pre>
            <pre>Email : {{item.last_name}}</pre>
            <pre>Foto : </pre>
            <img v-bind:src="item.avatar"><br>
            <a href="#"><h4 v-on:click="sukai">Sukai</h4></a>
            <br>
            <pre><img id="img1" v-bind:src="'https://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/Heart_coraz%C3%B3n.svg/1200px-Heart_coraz%C3%B3n.svg.png'"> {{suka}} menyukai</pre>
        </div>
    </div>
</template>
<script>
export default {
    name: 'FavoriteEmployee',
    data(){
        return{
            list_data:[],
            suka: 0
        }
    },
    mounted(){
        if(localStorage.list_data && localStorage.id_data){
            this.list_data = JSON.parse(localStorage.getItem('list_data'));
           
        }
    },
    methods:{
      sukai(){
        this.suka = this.suka+ 1;
      }
    }
}
</script>
    
<style>
    body {
  background: #fafafa;
  font-family: Arial, sans-serif;
  line-height: 1.6;
}

#img1{
  width: 15px;
}

h2 {
  margin-top: 0;
}

h3 {
  text-align: center;
}

.card {
  padding: 40px;
  background: #fff;
  max-width: 500px;
  border-radius: 20px;
  margin: 60px auto;
}

.highlight {
  font-weight: bold;
  color: #294;
}

.shadow1 { 
  box-shadow: 0 5px 10px rgba(154,160,185,.05), 0 15px 40px rgba(166,173,201,.2);
}

.shadow2 { 
  box-shadow: 0 7px 30px -10px rgba(150,170,180,0.5);
}
</style>