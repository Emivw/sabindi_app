<template>
    <ion-page>
      <ion-header>
        <ion-toolbar>
          <ion-title>Tab 1</ion-title>
        </ion-toolbar>
      </ion-header>
      <ion-content :fullscreen="true">
      <ion-grid>
         <ion-row>
          <ion-col></ion-col>
           <ion-col class="ion-align-items-center blue">
            <div class="container" id="container">
      <div class="form-container sign-up-container">
        <form>
          <h1 class="title">Create Account</h1>
          <span>or use your email for registration</span>
          <input type="text" placeholder="Name" />
          <input type="text" placeholder="Surname" />
          <input type="email" id="signUpEmail" placeholder="Email" />
          <input type="password" placeholder="Password" />
          <button type="submit">Sign Up</button>
        </form>
      </div>
  
      <div class="form-container sign-in-container">
        <form onSubmit={this.handleSubmitLogin}>
          <img src="https://i.postimg.cc/zf4jt9sC/Sabindi-Group-Global-Logo.png" alt=""/>
          <h1 class="title">Sign in</h1>
          <input type="email" id="signInEmail" placeholder="Email" />
          <input type="password" placeholder="Password" />
          <button type="submit">Sign In</button>
        </form>
      </div>
      
      <div class="overlay-container">
        <div class="overlay">
          <div class="overlay-panel overlay-left">
            <h1>Welcome Back!</h1>
            <p>To keep connected with us please login with your personal info</p>
            <button class="ghost" id="signIn" @click="login('x')">Sign In</button>
          </div>
          <div class="overlay-panel overlay-right">
            <h1>Hello, Friend!</h1>
            <p>Enter your personal details and start journey with us</p>
            <button class="ghost" id="signUp" @click="login('y')">Sign Up</button>
          </div>
        </div>
      </div>
    </div>
          </ion-col>
          <ion-col></ion-col>
         </ion-row>
      </ion-grid>
  
  
      </ion-content>
    </ion-page>
  </template>
  
  <script>
  import { defineComponent } from 'vue';
  import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
  // import ExploreContainer from '@/components/ExploreContainer.vue';
  
  export default  defineComponent({
    name: 'Tab1Page',
    components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage },
    methods: {
      login(result) {
      const container = document.getElementById('container');
  const signInEmail =  document.getElementById('signInEmail');
  const signUpEmail =  document.getElementById('signUpEmail');
  
    function openSignIn(){
      container.classList.remove("right-panel-active");
      if(signUpEmail.value !== ""){
        signInEmail.value = signUpEmail.value;
      }
    }
     console.log(result)
    function openSignUp(){
      container.classList.add("right-panel-active");
      if(signInEmail.value !== ""){
        signUpEmail.value = signInEmail.value;
      }
    }
  if( result == "y"){
    document.getElementById("signUp").addEventListener("click",openSignUp());
  }
  else{
  document.getElementById("signIn").addEventListener("click",openSignIn());
  }
    }
  }
  });
  
  
  </script>
  
  <style scoped>
  
   
  
  ion-row{
    height:88.4vh;
  }
  
  .blue{
    display:flex;
    align-items:center;
    justify-content:center;
    height:88.4vh;
  }
  
  ion-card{
    height:500px;
    width:550px;
  }
  
  @import url("https://fonts.googleapis.com/css?family=Montserrat:400,800");
  
  * {
    box-sizing: border-box;
  }
  
  
  
  h1 {
    font-weight: bold;
    margin: 0;
  }
  
  h2 {
    text-align: center;
  }
  
  p {
    font-size: 14px;
    font-weight: 100;
    line-height: 20px;
    letter-spacing: 0.5px;
    margin: 20px 0 30px;
  }
  
  span {
    font-size: 12px;
    color:black;
  }
  
  a {
    color: #333;
    font-size: 14px;
    text-decoration: none;
    margin: 15px 0;
  }
  
  button {
    border-radius: 2px;
    /* border: 3px solid black; */
    background-color: orange;
    color: #ffffff;
    font-size: 10px;
    font-weight: bold;
    padding: 10px 30px;
    letter-spacing: 1px;
    text-transform: uppercase;
    transition: transform 80ms ease-in;
  }
  
  button:active {
    transform: scale(0.95);
  }
  
  button:focus {
    outline: none;
  }
  
  button.ghost {
    background:  radial-gradient( #FEDB37 0%, #FDB931 12%, #9f7928 50%, #8A6E2F 60%, transparent 100%);
    border-color: #ffffff;
  }
  
  form {
    background-color: #ffffff;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    padding: 0 50px;
    height: 100%;
    text-align: center;
  }
  
  input {
    background-color: black;
    border: none;
    padding: 12px 15px;
    margin: 8px 0;
    width: 100%;
    color:white;
  }
  
  img{
  position:absolute;
  width:120px;
  top:13%;
  }
  .title{
    color:black
  }
  
  .container {
    background-color: #fff;
    border-radius: 10px;
    box-shadow: 0 14px 28px rgba(0, 0, 0, 0.25), 0 10px 10px rgba(0, 0, 0, 0.22);
    position: relative;
    overflow: hidden;
    width: 768px;
    max-width: 100%;
    min-height: 480px;
  }
  
  .form-container {
    position: absolute;
    top: 0;
    height: 100%;
    transition: all 0.6s ease-in-out;
  }
  
  .sign-in-container {
    left: 0;
    width: 50%;
    z-index: 2;
  }
  
  .container.right-panel-active .sign-in-container {
    transform: translateX(100%);
  }
  
  .sign-up-container {
    left: 0;
    width: 50%;
    opacity: 0;
    z-index: 1;
  }
  
  .container.right-panel-active .sign-up-container {
    transform: translateX(100%);
    opacity: 1;
    z-index: 5;
    animation: show 0.6s;
  }
  
  @keyframes show {
    0%,
    49.99% {
      opacity: 0;
      z-index: 1;
    }
  
    50%,
    100% {
      opacity: 1;
      z-index: 5;
    }
  }
  
  .overlay-container {
    position: absolute;
    top: 0;
    left: 50%;
    width: 50%;
    height: 100%;
    overflow: hidden;
    transition: transform 0.6s ease-in-out;
    z-index: 100;
  }
  
  .container.right-panel-active .overlay-container {
    transform: translateX(-100%);
  }
  
  .overlay {
    background: #ff416c;
    background: -webkit-linear-gradient(to right, #ff4b2b, #ff416c);
    background: linear-gradient(to right, 	grey, 	black);
    background-repeat: no-repeat;
    background-size: cover;
    background-position: 0 0;
    color: #ffffff;
    position: relative;
    left: -100%;
    height: 100%;
    width: 200%;
    transform: translateX(0);
    transition: transform 0.6s ease-in-out;
  }
  
  .container.right-panel-active .overlay {
    transform: translateX(50%);
  }
  
  .overlay-panel {
    position: absolute;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    padding: 0 40px;
    text-align: center;
    top: 0;
    height: 100%;
    width: 50%;
    transform: translateX(0);
    transition: transform 0.6s ease-in-out;
  }
  
  .overlay-left {
    transform: translateX(-20%);
  }
  
  .container.right-panel-active .overlay-left {
    transform: translateX(0);
  }
  
  .overlay-right {
    right: 0;
    transform: translateX(0);
  }
  
  .container.right-panel-active .overlay-right {
    transform: translateX(20%);
  }
  
  .social-container {
    margin: 20px 0;
  }
  
  .social-container a {
    border: 1px solid #dddddd;
    border-radius: 50%;
    display: inline-flex;
    justify-content: center;
    align-items: center;
    margin: 0 5px;
    height: 40px;
    width: 40px;
  }
  
  footer {
    background-color: #222;
    color: #fff;
    font-size: 14px;
    bottom: 0;
    position: fixed;
    left: 0;
    right: 0;
    text-align: center;
    z-index: 999;
  }
  
  footer p {
    margin: 10px 0;
  }
  
  footer i {
    color: red;
  }
  
  footer a {
    color: #3c97bf;
    text-decoration: none;
  }
  
  </style>
  