<template>
  <div class="home container-fluid">
    <div class="row">
      <div class="col-4">
   <form @submit.prevent="translateRaw()" class="form-inline">
          <div class="form-group">
            <input type="text" placeholder="Type SQL statment..." class="form-control" v-model="newRequest.body" required />
          </div>
<button type="submit" class="btn btn-success m-2" @submit.prevent="translateRaw()">Translate</button>
        </form>
      </div>
      <div class="col-3 m-2 card translated">
        plain english here: {{translated}}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "home",
  props: [],
  data(){
    return {
      newRequest:{
        body:""
      },
      translated: ""
      //NOTE will probably be adding to string of translated (like palendrome whiteboard)
    }
  },
  mounted(){

  },
  methods:{
    translateRaw(){
      let todo = this.newRequest.body
      if(todo == "spencer"){
        this.translated = "yes"
        }
        else this.translated = "no"
    }

  }
};
</script>
<style>

</style>
