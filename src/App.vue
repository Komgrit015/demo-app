<template>
  <section>
      <img :src="picture" :width="size" :height="size" ref="imageEl"> <br>
      <!-- Nickname : <input type="text" v-on:input="setNickname"/> -->

      <form @submit.prevent="submitForm">
          <label>Nickname : </label>
          <!-- <input type="text" v-on:input="setNickname" ref="nicknameEl"/> -->
          <input type="text" ref="nicknameEl"/>
          <button type="submit"> Submit </button>
      </form>

      <h1>Name : {{ getFullname() }}</h1>
      <h1>Lastname {{ lastName }}</h1>
      <h2>Nickname {{ nickname }}</h2>
      <h1>Age {{ age }}</h1>

      <p>Address : <span v-html="address"></span></p>
      <p>Social: <a :href="social">FaceBook</a></p> 
      <p>Hobby</p>
      <ul>
        <li>{{ hobby[0] }}</li>
        <li>{{ hobby[1] }}</li>
        <li>{{ hobby[2] }}</li>

      </ul>
      <p>Data</p>
        <ul>
          <li>Gender: {{ general.gender }}</li>
          <li>Weight: {{ general.weight }} KG</li>
          <li>Height: {{ general.height }} CM</li>
          <li>Status: {{ general.status }}</li>
        </ul>
        <button v-on:click="showData">Click</button>
        <button @click="increment(10)">Add</button>
        <button @click.middle="decrement">Down</button>


  </section>
</template>

<script>
export default {
  name: 'App',
  data(){
    return {
      firstName:"Komgrit",
      lastName:"Studio",
      nickname:"",
      age:27,
      address:"<strong>Test</strong>",
      picture: "https://cdn-icons-png.flaticon.com/512/8893/8893995.png",
      size:50,
      social: "https://www.flaticon.com",
      hobby:["Test","Football","Music"],
      general:{gender:"men", weight:70, height:170, status:false}
    }
  },
  methods:{
    getFullname(){
      // return this.firstName + this.lastName
      return `${this.firstName} ${this.lastName}`
    },
    showData(){
      alert(this.firstName)
    },
    increment(value){
      this.age+=value
    },
    decrement(){
      this.age--
    },
    // setNickname(event){
    //   // console.log(event.target.value)
    //   this.nickname = event.target.value

    // },
    submitForm(){
      // alert("Success")
      // console.log(this.$refs.imageEl) ;
      this.nickname = this.$refs.nicknameEl.value;
    
    }
  }
}
</script>

<style>

</style>
