<template>
    <div>
        <br>
        <h1>Employee List</h1>
        <table>
           <thead>
                <tr>
                <th>Id</th>
				<th>Avatar</th>
                <th>Email</th>
                <th>First name</th>
                <th>Last name</th>
                <th>Detail</th>
            </tr>
           </thead>
            <tbody>
                <tr v-for="item in list" v-bind:key="item.id">
                <td>{{item.id}}</td>
				<td><img v-bind:src="item.avatar"></td>
                <td>{{item.email}}</td>
                <td>{{item.first_name}}</td>
                <td>{{item.last_name}}</td>
                <td><router-link :to="{ path: '/detail/'+ item.id}"><Button class="button">Detail</Button></router-link></td>
            </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import Vue from 'vue';
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios,axios)

export default {
    name: "EmployeeList",
    data(){
        return {list:undefined}
    },
    mounted(){
        Vue.axios.get('https://reqres.in/api/users')
        .then((response)=>{
            this.list = response.data.data
            console.warn(response)
        })
    }

}
</script>
<style>
h1{
    text-align: center;
}
    table { 
	width: 750px; 
	border-collapse: collapse; 
	margin:50px auto;
	}

/* Zebra striping */
tr:nth-of-type(odd) { 
	background: #eee; 
	}

th { 
	background: #3498db; 
	color: white; 
	font-weight: bold; 
	}

td, th { 
	padding: 10px; 
	border: 1px solid #ccc; 
	text-align: left; 
	font-size: 18px;
	}

/* 
Max width before this PARTICULAR table gets nasty
This query will take effect for any screen smaller than 760px
and also iPads specifically.
*/
@media 
only screen and (max-width: 760px),
(min-device-width: 768px) and (max-device-width: 1024px)  {

	

	/* Force table to not be like tables anymore */
	table, thead, tbody, th, td, tr { 
		display: block; 
	}
	
	/* Hide table headers (but not display: none;, for accessibility) */
	thead tr { 
		position: absolute;
		top: -9999px;
		left: -9999px;
	}
	
	tr { border: 1px solid #ccc; }
	
	td { 
		/* Behave  like a "row" */
		border: none;
		border-bottom: 1px solid #eee; 
		position: relative;
		padding-left: 50%; 
	}

	td:before { 
		/* Now like a table header */
		position: absolute;
		/* Top/left values mimic padding */
		top: 6px;
		left: 6px;
		width: 45%; 
		padding-right: 10px; 
		white-space: nowrap;
		/* Label the data */
		content: attr(data-column);

		color: #000;
		font-weight: bold;
	}

}

.button {
	cursor: pointer;
	width: 150px;
	height: 25px;
	align-items: center;
	justify-content: center;
	position: relative;
  z-index: 1;
  overflow: hidden;
	font-size: 15px;
	font-weight: 300;
	letter-spacing: 2px;
	color: #ffffff;
	border-radius: 7px;
	padding: 20px 45px;
	box-shadow:
  0 0px 10px rgba(221, 160, 221, 0.25),
  0 0px 15px rgba(39, 39, 175, 0.418),
  0 0px 35px rgba(25, 25, 112, 0.55);
}

.button::before {
	content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 200%;
	background: linear-gradient(to bottom right, #191970, #DDA0DD);
	transition: transform 0.4s;
  z-index: -1;
}

.button:hover::before {
  transform: translateY(-20%);
}
</style>