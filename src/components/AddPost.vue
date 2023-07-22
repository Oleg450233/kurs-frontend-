<template>
<form @submit.prevent="createPost" :class="{error:maxCharacter>20}">
  <label for="title">Название статьи</label>
  <input v-model="userTitleInput" type="text" id="title" placeholder="Введите название статьи">
  <label for="text">Основной текст {{maxCharacter}}/20</label>
  <textarea v-model="userText" id="text" placeholder="Введите основной текст"></textarea>
  <button>Добавить</button>
</form>
  </template>
<script>
export default {
  name:"AddPost",
  data(){
    return {
      userTitleInput:"",
      userText:"",
      };
  },
  methods:{
    createPost(){
      if(this.userTitleInput!==""&& this.userText!==""){
this.$emit("add-post",this.userText,this.userTitleInput);
        this.userTitleInput="";
        this.userText="";
      }
    },
  },
  computed:{
    maxCharacter(){
      return this.userText.length;
    }
  }
};
</script>

<style scoped>

form{
  width: 20%;
  float: right;
  position: absolute;
  top: 80px;
  right:2.5%;
  margin-right: 10%;
}

form #title,form textarea {
  width: 100%;
  resize: vertical;
  font-size: 16px;
  border-radius: 5px;
  background: #aaa771;

  outline: none;

}
form label{
  font-size: 18px;
  color:green;
}
form.error label {
  color: red;
}
form #title{
  margin-bottom: 20px;
}
form textarea{
  height: 100px;
}
form button{
  background: #aaa771;
  border:2px solid #5e5b21;
  border-bottom-width:4px ;
  padding: 10px 12px;
  font-size: 13px;
  font-weight: bold;
  color:#5e5b21;
  border-radius: 5px;
  cursor: pointer;
  transition: all 500ms ease;
  margin-top: 10px;
  float: right;
}
</style>