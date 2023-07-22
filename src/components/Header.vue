<template>

  <div   id="header">
    <div class="bg">
    <span class="logo">{{title}}</span>
    <p class="user">{{fullname}} ({{user.rating}})    <button @click="addRating">+</button></p>

    </div>
  </div>



</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      user:
          {
            name: "Oleg",
            surname: "Uvarov",
            age: 20,
            rating: 0,
            email: "nachalnikovk@mail.ru"
          },
      allRating:0,
    };
  },
  computed:{
    fullname(){
      return `Привет,${this.user.name} ${this.user.surname}`;
    }
  },
  methods:{
    addRating(){
      this.user.rating++;
      this.allRating++;
    }

  },
  mounted(){
    this.addRating();
  },
  watch: {
    allRating(newValue, oldValue) {
      if (newValue > 5)
        alert("I am an alert box!");
    },
  },
  props:{
    title:{
      type:String,
      required:true,
    },
  },
};

</script>
<style scoped>

#header{

  background: #333;
  color:#fff;

  border-bottom: 2px solid #000;





}
.bg{
  padding: 20px;
  display: flex;
  width: 95%;
  margin: 0 2.5%;
  justify-content: space-between;
  align-items: center;
}
#header .logo{

  font-size: 20px;
}
.user button{
border:0;
  padding:10px 15px;
  border-radius: 5px;
  background: red;
  font-size: 15px;
  color:white;
  font-weight: bold;
  cursor: pointer;
  margin-left: 5px;
  position: relative;
  top:-2px;
}

.user button:hover {
background: palevioletred;
}
</style>