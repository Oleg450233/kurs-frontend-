
<template>
  <main>
  <div   id="articles">
    <div v-if="articles.length>0" class="post" v-for="el in articles" :key="el.id">
      <button @click="deletePost(el.id)">Удалить</button>
      <h2>{{el.title}}</h2>
      <p>{{el.text}}</p>
    </div>
    <h1 class="empty" v-else>Статей нет</h1>
  </div>
</main>
  <aside>
     <AddPost v-on:add-post="createPost"/>
  </aside>

</template>

<script>
import AddPost from "./AddPost.vue";
export default {
  name:"Articles",
  components:{
    AddPost,
  },
  data(){
    return {
        articles:[
        {
          id: 1,
          title: "Google",
          text: "Привет мир",
        },
        {
          id: 2,
          title: "Apple",
          text: "Привет Apple",
        },
        {
          id: 3,
          title: "Samsung",
          text: "Привет Samsung",
        },
      ],

    };
  },
  methods:{
      deletePost(id){
        this.articles=this.articles.filter((el)=>el.id !==id);
      },
    createPost(userTitleInput,userText){

          this.articles.unshift({
            id:Math.random()*1000,
            title:userTitleInput,
            text:userText,
          });
    },
  },
};

</script>


<style scoped>

#articles {
  margin: 20px;

}
#articles .post{
  background: #c6c391;
  padding: 20px;
  margin-bottom: 20px;
  border: 1px solid red;
  color:#5e5b21;
  width: 60%;
  float: left;

}
#articles .post button{
  float:right;
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
  }
#articles .post button:hover{
  margin-top: 2px;
  border-bottom-width: 2px;
}
.empty {
  margin: 20px;
  color: red;
}
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