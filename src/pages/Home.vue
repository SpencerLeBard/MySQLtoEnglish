<template>
  <div class="home container-fluid">
    <div class="row">
      <div class="col-4">
   <form @submit.prevent="translateRaw()" class="form-inline">
          <div class="form-group">
            <input type="text" placeholder="Type MySQL statment..." class="form-control" v-model="newRequest.body" required />
          </div>
<button type="submit" class="btn btn-success m-2" @submit.prevent="translateRaw()">Translate</button>
        </form>
      </div>
      <div class="col-3 m-2 card translated">
        plain english here: <br> {{translated}}
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
          }
  },
  methods:{
    translateRaw(){
      //NOTE option: could call new methods in if statments
      let translated = ""
      let todo = this.newRequest.body
      let res = todo.split(" ")
      for(let i=0;i<res.length;i++){
        let word = res[i].toLowerCase()
        let selectKeyword = res[i + 1] 
        let fromKeyword = "test"
        let truncateKeyword = "test"
      if(word == "select"){
        this.translated += "Getting all" + " " + selectKeyword
        }
      if(word == "from"){
          let fromKeyword = res[i+1] 
          this.translated += " " + "from table" + " " + fromKeyword
        }
      if(word == "insert"){
          let insertKeyword = res[i+1] 
          this.translated += " Adding " + insertKeyword + " " + "Into Table"
        }
      if(word == "truncate"){
          let truncateKeyword = res[i+2] 
          debugger
          this.translated += " DELETE EVERYTHING IN " + truncateKeyword + " " + "Table"
        }
        // else this.translated = "Cannot Detect MySQL Syntax"
    }
    }
  }
};
</script>
<style>

</style>
