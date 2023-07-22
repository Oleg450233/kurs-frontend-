<template>
  <Header title="itProger"/>
<Articles/>

</template>


<script>
import Articles from "./components/Articles.vue";
import Header from "./components/Header.vue";

export default {
  components:{
    Header,Articles
  },

};
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  background: #fcfcfc;
}
</style>