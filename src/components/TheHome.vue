<template>
    <div> 
         <nav class="navbar navbar-light bg-light">
            <a class="navbar-brand"></a>
                <form class="form-inline">
                    <button 
                    class="btn btn-outline-info my-2 my-sm-0"
                    type="submit"
                    @click.prevent="logOutUser"
                    >Salir
                    </button>
                </form>
        </nav>

        <div class="container mt-5">
        <table class="table table-striped table-bordered">
            <thead class="thead-dark">
                <tr>
                    <th style="width: 50%" scope="col-6">
                        <div style="social_icon_user">
                            <i class="far fa-user" style="color: white;"></i>                            
                            <span style="margin-left: 10px">Name</span>
                        </div>
                    </th>
                    <th style="width: 50%" scope="col-6">
                        <div style="social_icon_mail">
                            <i class="far fa-envelope" style="color: white;"></i>                            
                            <span style="margin-left: 10px">Email</span>
                        </div>
                    </th>                                 
                    
                </tr>
            </thead>
            <tbody>
                <tr>
                    <th scope="row">
                        <div style="social_icon">
                                <i class="fas fa-user-check" style="font-size:20px; color:green"></i>                            
                                <span style="margin-left: 10px">{{user.name}}</span>
                        </div>
                    </th>                
                    <td>{{user.email}}</td>                
                </tr>
                
            </tbody>
        </table>

        </div>   

    </div>    
    
</template>

<script>

import VueJwtDecode from 'vue-jwt-decode';

export default {
    data(){
        return{
            user: {  }
        }
    },
    methods:{

        logOutUser(){
            localStorage.removeItem('jwt');
            localStorage.removeItem('user');
            this.$router.push('/');
        },
        getUserData(){
            let token = localStorage.getItem('jwt');
            // let user = localStorage.getItem('user'); Se cambio por la informacion que entrega el token
            let user = VueJwtDecode.decode(token);
            console.log(user);
            // this.user = JSON.parse(user);
            this.user = user;
            console.log(this.user);
        }
    },
    
    created() {

        this.getUserData();

    }
    
}
</script>

<style scoped>

</style>