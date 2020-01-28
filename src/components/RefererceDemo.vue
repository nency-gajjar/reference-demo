<template>
  <div>
    <label for="email">Email :</label>
    <input type="email" ref="input" v-model="email" id="check" />
    <input type="button" value="submit" @click="submit" />
    <p ref="error">{{checkEmail}}</p>
    <hr/>
    <p v-for="i in 5" :key="i" ref="item">Item no. {{ i }}</p>
    <input type="button" value="Click" @click="clickMe" />
    <hr />

    <select ref="dropdown">
      <option value="volvo">Volvo</option>
      <option value="saab">Saab</option>
      <option value="opel">Opel</option>
      <option value="audi">Audi</option>
    </select>
    <input type="button" value="getValue" @click="getValue"/>
    <br><br><hr>
    <input type="button" ref="btnChange" v-model="name" value="change" @click="changeName"/>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      checkEmail: "",
      counter: 0,
      value: '',
      name: 'I get Changed'
    };
  },

  methods: {
    submit() {
      var checkEmailString = this.email.match(
        /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/g
      );
      if (this.email != null && this.email.length > 0) {
        if (this.email.match(checkEmailString)) {
          //code
          this.checkEmail = this.email;
          this.$refs.input.style = "border: 2px solid green";
          this.$refs.input.attributes;
        } else {
          console.log((this.checkEmail = "Please enter valid email..."));
          this.$refs.input.style = "border: 2px solid red";
          this.$refs.error.style = "background-color :yellow";
          return;
        }
      } else {
        console.log((this.checkEmail = "Please enter email..."));
        this.$refs.input.style = "border: 2px solid red";
        this.$refs.error.style = "background-color :yellow";
        return;
      }
    },

    clickMe() {
      console.log(this.$refs.item[1].style = "background-color :powderblue");
      
    },

    getValue(){
        console.log(this.$refs.dropdown.value)
    },

    changeName(){
        console.log(this.$refs.btnChange);
        this.$refs.btnChange.innerText  = this.name
    }
    
  }
};
</script>

<style scoped>
select{
    padding: 2px;
}
</style>