<template>
   
    <img src="../assets/logo12.png" alt="logo">

    <h1>Sign Up!</h1>

    <div class="register">
        <input type="text" v-model="name" placeholder="Enter Name" class="frm">
        <input type="text" v-model="email" placeholder="Enter Email" class="frm" >
        <input type="password" v-model="password" placeholder="Enter Password" class="frm">
        <button class="btn1" v-on:click="signUp">Sign Up</button>
    </div>
</template>


<script>

import axios from 'axios'

    export default{
        name: 'SignUp',
        data(){
            return{
                name:'',
                email:'',
                password:'',
            }
        }
        ,
        methods:{
           async signUp(){

                let result = await axios.post('http://localhost:3000/user',{
                    name:this.name,
                    email:this.email,
                    password:this.password,
                }); 


                console.warn(result);

                if(result.status==201){
                    alert('Congrats SignUp Done! And Credentials stored in Database.')
                    // localStorage.setItem('User Info', JSON.stringify(result.data))
                }

                else{
                    alert('OOh! There is an Error.')
                }
                // console.warn('Your Data is: ' , this.name, this.email, this.password)
            }
        }
    }

</script>

<style>
/* *{
    background: url(../assets/pic14.jpg);
    background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  transition: 0.4s;
  
} */
.register , .frm {
   height:40px;
   width: 300px;
   padding-left: 20px;
   display: block;
   margin-left: auto;
   margin-right: auto;
   margin-bottom: 30px;
   font-size: 17px;
   
}

.frm , .btn1{
    border: 1px solid rgb(44, 44, 44);
    border-radius: 5px;
    box-shadow: rgba(0, 0, 0, 0.144) 0px 5px 15px;
}

.btn1{
    display: block;
   margin-left: auto;
   margin-right: auto;

    width: 320px;
    height: 45px;
    padding: 20px 20px 20px px;
    font-size: 17px;
    cursor: pointer;
    background: rgb(17, 17, 17);
    color: #fff;
}

.btn1:hover{
    color: rgb(17, 17, 17);
    background: rgba(255, 255, 255, 0);
}

</style>