<template>

<div class="FondoPantalla">
<div class="container">
    <div class="d-flex justify-content-center h-100">
        <div class="card">
            <div class="card-header">
                <h3>Sign in</h3>
                
            </div>
            <div class="card-body">
            <form>
                <div class="input-group form-group">
                    <div class="input-group-prepend">
                        <span class="input-group-text"><i class="fas fa-user"></i></span>
                    </div>

                    <input type="email" class="form-control" placeholder="email address" v-model= "login.email">						
                </div>

                <div class="input-group form-group">
                    <div class="input-group-prepend">
                        <span class="input-group-text"><i class="fas fa-key"></i></span>
                    </div>
                    <input type="password" class="form-control" placeholder="password" v-model= "login.password">
                </div>
                
                <!-- <div class="row align-items-center remember">
                    <input type="checkbox">Remember Me
                </div> -->
                <div class="form-group">
                    <!-- <input type="submit" value="Login" class="btn float-right login_btn"> -->
                    <button type="submit" class="btn float-right login_btn" @click.prevent="loginUser" >Login</button>
                </div>
            </form>
			</div>
			<div class="card-footer">
				<div class="d-flex justify-content-center links">
					Equipo 94   Ciclo 3 Sprint 3
				</div>
                <div class="d-flex justify-content-end social_icon">                    
                    <a title="Github" href="https://github.com/pacho20lucho/Retociclo3semana3"><i class="fab fa-github-square"></i></a>
                </div>
			</div>
		</div>
	</div>
</div> 
</div>
    
</template>


<script>
import swal from 'sweetalert';
import VueJwtDecode from 'vue-jwt-decode';


export default {
    data() {

        return{
            login: {
                email:'',
                password:''
            }
        }
    },
    methods:{

        async loginUser(){
            try{

                // console.log(this.login);
                // let response = await this.$http.post('/api/usuario/login', this.login);
                let response = await this.$http.post('/api/auth/signin', this.login);
                console.log(response.data);

                // Se debe revisar si esta accessToken en el backend 
                let token = response.data.accessToken;


                // Se incluyo igual que en TheHome despues de tener la informacion del token con let token se decodifica con el VueJwtDecode en esta linea para tener la inf del user
                let user = VueJwtDecode.decode(token);


                // En el controller del Backend el token solo entrega token. 
                // let user = response.data.user;

                localStorage.setItem('jwt', token);



                // En el controller del Backend el token solo entrega token. 
                // localStorage.setItem('user',JSON.stringify(user));


                if(token) {
                    swal("Login correcto", `Los datos son correctos, bienvenido ${user.name}!`,"success");
                    this.$router.push('/home');
                }
            }
            catch(error){
                swal("Ooops!","Algo salió mal!","error");
                console.log(error)
            }
                        

        }
    }    
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Numans');

.FondoPantalla{
/* background-image: url('http://getwallpapers.com/wallpaper/full/a/5/d/544750.jpg'); */
/* background-image: url('http://getwallpapers.com/wallpaper/full/9/4/5/12467.jpg'); */
/* background-image: url('http://getwallpapers.com/wallpaper/full/2/a/c/12644.jpg'); */
/* background-image: url('http://getwallpapers.com/wallpaper/full/1/9/5/12638.jpg'); */
/* background-image: url('http://getwallpapers.com/wallpaper/full/6/1/e/44051.jpg'); */
background-image: url('http://getwallpapers.com/wallpaper/full/0/1/4/44267.jpg');

/* background-image: url('http://getwallpapers.com/wallpaper/full/9/d/0/12413.jpg'); */
/* background-image: url('http://getwallpapers.com/wallpaper/full/2/7/2/12470.jpg'); */

background-size: cover;
background-repeat: no-repeat;
height: 100%;
font-family: 'Numans', sans-serif;

position:fixed;
padding:0;
margin:0;

top:0;
left:0;

width: 100%;
height: 100%;
}

.container{
height: 100%;
align-content: center;
}

.card{
height: 370px;
margin-top: auto;
margin-bottom: auto;
width: 400px;
background-color: rgba(0,0,0,0.5) !important;
}

.social_icon a{
font-size: 28px;
margin-left: 10px;
color: #f5f5f8;
}

.social_icon a:hover{
color: rgb(26, 24, 24);
cursor: pointer;
}

.card-header h3{
color: white;
}

.social_icon{
position: absolute;

right: 55px;
top: 323px;

}

.input-group-prepend span{
width: 50px;
background-color: #FFC312;
color: black;
border:0 !important;
}

input:focus{
outline: 0 0 0 0  !important;
box-shadow: 0 0 0 0 !important;

}

.remember{
color: white;
}

.remember input
{
width: 20px;
height: 20px;
margin-left: 15px;
margin-right: 5px;
}

.login_btn{
color: black;
background-color: #FFC312;
width: 100px;
}

.login_btn:hover{
color: black;
background-color: white;
}

.links{
color: white;
}

.links a{
margin-left: 4px;
}

</style>
