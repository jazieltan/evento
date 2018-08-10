<template>
  <div class="container">
    <h1>Evento</h1>
    <p>Simply let us know when you are available</p>
      <form >
        <input id="inputName" type="text" placeholder="what is your name?" v-model="name">
        <label for="date1">17th August 2018
        <input id="date1" name="date1" type="checkbox" v-model="dates" value="17th August"></label>
        <label for="date2">24th August 2018
        <input id="date2" name="date2" type="checkbox" v-model="dates" value="24th August"></label>
        <button class="btn btn-primary" @click.prevent="addEntry()">Submit!</button>
      </form>
      <h1></h1>
    <ul>
      <li v-for="(entry, key) in entries" :key="entry.key" class="entries">
          <div class="name">{{key}}: {{entry.name}}</div>
          <div class="dates">
            <span>{{entry.dates[0]}}</span>
            <span>{{entry.dates[1]}}</span>
          </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'SetDate',
    data () {
    return {
      name: '',
      dates: [],
      entries: [
      ]
    }
  },
  methods: {
    addEntry () {
      let inputName = document.getElementById('inputName')
      if(this.name != '' && this.dates != ''){
        this.entries.push({
          name: this.name,
          dates: this.dates
        })
        this.name =''
        inputName.classList.remove('inputError')
        inputName.placeholder='what is your name?'
      }
      else if(this.name == ''){
        inputName.classList.add('inputError')
        inputName.placeholder='You forgot your name!'
      }
      else if(this.dates == ''){
        this.entries.push({
          name: this.name,
          dates: ['not available']
        })
      }

      // let checkboxes = document.querySelectorAll('input[type=checkbox]')
      // checkboxes.forEach(checkbox  => {
      //   checkbox.checked = false;
      // });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
$lightGray: #eee;
$darkGray: #666;
$blue: #65c1ff;
$red: #ff2a46;
$green: #2ce263;
.container{
  width: 9  0%;
  margin: 0 auto;
}
button{
  background: $green;
  border: none;
  color: white;
  padding: 10px;
  font-size: 1.2rem;
  width: 100%;
  margin-bottom: 5px;
  box-sizing: border-box
}
h3 {
  margin: 40px 0 0;
}
ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}
.entries {
  .name{
    padding: 10px;
  }
  .dates{
    background: $lightGray;
    display: flex;
    flex: 2;
    padding: 10px;
    span{
      flex: 1;
    }
  }
}

ul li {
  font-size: 1.3em;
  background-color: white;
  margin-bottom: 2px;
  border-bottom: 1px solid $blue;
  color: $darkGray;
  text-align: left;
}
input[type="text"]{
  border: 1px solid $blue;
  background: #fefefe;
  padding: 20px;
  font-size: 1.2em;
  color: $darkGray;
  display: block;
  width: 100%;
  box-sizing: border-box;

  &.inputError{
    background: lightpink;
    border: 1px solid $red;
  }
}
label {
  display: block;
  padding: 20px;
  background: $lightGray;
  font-size: 1.2rem;
  margin: 5px 0;
}
label:hover{
  background: $blue
}
</style>
