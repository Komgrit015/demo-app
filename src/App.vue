<template>
  <section>
    <img :src="picture" :width="size" :height="size" ref="imageEl" /> <br />
    <!-- Nickname : <input type="text" v-on:input="setNickname"/> -->

    <!-- <form @submit.prevent="submitForm">
          <label>Nickname : </label>
          <input type="text" v-on:input="setNickname" ref="nicknameEl"/>
          <input type="text" ref="nicknameEl"/>
          <button type="submit"> Submit </button>
      </form> -->

    <h1>Name : {{ getFullname }}</h1>
    <h1>Lastname {{ lastName }}</h1>
    <!-- <h2>Nickname {{ nickname }}</h2> -->
    <h1>Age {{ age }}</h1>
    <h1>Salary : {{ salary }} ฿ </h1>
    <h1>Salary/Year : {{ getIncome}} ฿ </h1>
    <h1>Department : {{ getDepartment  }}</h1>

    <button @click="addSalary(5000)">Add Salary</button>
    
    <!-- <h2>Method1 : {{ getRandomByMethod() }}</h2>
    <h2>Method2 : {{ getRandomByMethod() }}</h2>
      <hr>
    <h2>Computed1 : {{ getRandomByComputed }}</h2>
    <h2>Computed2 : {{ getRandomByComputed }}</h2> -->



    <button @click="toggleVisible">{{ isVisible ? "Hide" : "Display" }} Detail</button>  
    <article v-show="isVisible">
      <p>Address : <span v-html="address"></span></p>
      <p>Social: <a :href="social">FaceBook</a></p>
      <p v-if="hobby.length === 0">No Hobby</p>
      <div v-else>
        <p>Hobby</p>
        <ul>
          <li v-for="(item, index) in hobby" :key="index">{{ item }}</li>
          <!-- <li>{{ hobby[0] }}</li>
            <li>{{ hobby[1] }}</li>
            <li>{{ hobby[2] }}</li> -->
        </ul>
      </div>
      <p>Data</p>
      <ul>
        <!-- <li>Gender: {{ general.gender }}</li>
            <li>Weight: {{ general.weight }} KG</li>
            <li>Height: {{ general.height }} CM</li>
            <li>Status: {{ general.status }}</li> -->
        <li v-for="(item, key) in general" :key="key">{{ key }} - {{ item }}</li>
      </ul>
    </article>

    <!-- event -->
    <!-- <button v-on:click="showData">Click</button>
        <button @click="increment(10)">Add</button>
        <button @click.middle="decrement">Down</button> -->
  </section>
</template>
test
<script>
export default {
  name: "App",
  data() {
    return {
      firstName: "Komgrit",
      lastName: "Studio",
      nickname: "",
      age: 27,
      address: "<strong>Test</strong>",
      picture: "https://cdn-icons-png.flaticon.com/512/8893/8893995.png",
      size: 50,
      social: "https://www.flaticon.com",
      hobby: ["Test", "Football", "Music", "Music", "Music"],
      general: { gender: "men", weight: 70, height: 170, status: false },
      isVisible:false,
      salary: 20000
    };
  },
  methods: {
   
    toggleVisible(){
        this.isVisible = !this.isVisible;
    },
    addSalary(value){
      this.salary += value;
    }
    // getRandomByMethod(){
    //     return Math.random();
    // }
    // showData(){
    //   alert(this.firstName)
    // },
    // increment(value){
    //   this.age+=value
    // },
    // decrement(){
    //   this.age--
    // },
    // setNickname(event){
    //   // console.log(event.target.value)
    //   this.nickname = event.target.value

    // },
    // submitForm(){
    //   // alert("Success")
    //   // console.log(this.$refs.imageEl) ;
    //   this.nickname = this.$refs.nicknameEl.value;

    // }
  },
  computed:{
    getFullname() {
      // return this.firstName + this.lastName
      return `${this.firstName} ${this.lastName}`;
    },
    getIncome(){
      return this.salary * 12 ;
    },
    getDepartment(){
      return this.salary >= 35000 ? "Project manager " : "Programmer"
    }
    // getRandomByComputed(){
    //     return Math.random();
    // }
  },
  watch:{
    salary(value){
      if(value > 50000){
        alert("Salary should not exceed 50,000 ฿")
        setTimeout(()=>{
          this.salary = 50000
        },2000)
      }
    }
  }
};
</script>

<style>
</style>
