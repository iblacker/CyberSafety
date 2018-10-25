<template>
    <div class="holder">
      <h1>Create Course</h1>
          <div>
            <b-form @submit="onSubmit" @reset="onReset" v-if="show">

              <b-form-group id="exampleInputGroup2"
                            label="Author Name:"
                            label-for="exampleInput2"
                            description="Enter the name of the course author.">
                <b-form-input id="exampleInput2"
                              type="text"
                              v-model="form.name"
                              required
                              placeholder="">
                </b-form-input>
              </b-form-group>

              <b-form-group id="exampleInputGroup1"
                            label="Description:"
                            label-for="exampleInput1"
                            description="Enter a description about the course.">
                <b-form-input id="exampleInput1"
                              type="description"
                              v-model="form.description"
                              required
                              placeholder="">
                </b-form-input>
              </b-form-group>


              <b-form-group id="exampleInputGroup3"
                            label="Grade:"
                            label-for="exampleInput3">
                <b-form-select id="exampleInput3"
                              :options="grades"
                              required
                              v-model="form.grade">
                </b-form-select>
              </b-form-group>


              <b-form-group id="exampleInputGroup4"
                            label="Module:"
                            label-for="exampleInput3">
                <b-form-select id="exampleInput3"
                              :options="modules"
                              required
                              v-model="form.module">
                </b-form-select>
              </b-form-group>
              <b-button type="reset" variant="danger">Reset</b-button>
              <b-button type="submit" variant="primary">Submit</b-button>
            </b-form>
            </div>

          </div>
          <!-- <button v-on:click = "addQuiz()">Add Quiz</button>
          <button v-on:click = "addVideo()">Add Video</button>
          <button v-on:click = "addImage()">Add Image</button>
          <button v-on:click = "addAudio()">Add Audio</button>
          <button v-on:click = "addPresentation()">Add Presentation</button>
          <router-link to="/TextModule">Add Text</router-link> -->
          <!-- <ul>
            <transition-group name="list" enter-active-class="animated bounceInDown" leave-active-class="animated bounceOutDown">
              <li v-for="(data, index) in modules" :key='index'> {{ data.module }}
                <i class="fa fa-window-close" v-on:click="remove(index)"></i>
                <i class="fa fa-edit" v-on:click="editModule()"></i>
                <i class="fa fa-drivers-license" v-on:click="viewModule()"></i>
              </li>
            </transition-group>
          </ul> -->
          <!-- <button v-on:click = "viewCourse()">View Course</button>
          <button v-on:click = "submitCourse()">Submit Course</button> -->
</template>

<script>
export default {

  name: 'Modules',
  data() {
    return {
      form: {
        description: '',
        name: '',
        module: null,
        grade: null
      },
      grades: [
        { text: 'Select One', value: null },
        'Grade 1', 'Grade 2', 'Grade 3', 'Grade 4'
      ],
      modules: [
        { text: 'Select One', value: null },
        'Video', 'Image', 'Audio', 'Presentation', 'Text'
      ],
      show: true
    }
  },

  methods: {
    onSubmit (evt) {
      evt.preventDefault();
      alert(JSON.stringify(this.form));
    },
    onReset (evt) {
      evt.preventDefault();
      /* Reset our form values */
      this.form.description = '';
      this.form.name = '';
      this.form.grade = null;
      /* Trick to reset/clear native browser form validation state */
      this.show = false;
      this.$nextTick(() => { this.show = true });
    },
    addQuiz() {
          alert("Content coming soon!");
          this.modules.push({module: "Quiz"});
    },
    addVideo() {
          alert("Content coming soon!");
          this.modules.push({module: "Video"});
    },
    addImage() {
          alert("Content coming soon!");
          this.modules.push({module: "Image"});
    },
    addAudio() {
          alert("Content coming soon!");
          this.modules.push({module: "Audio"});
    },
    addPresentation() {
          alert("Content coming soon!");
          this.modules.push({module: "Presentation"});
    },
    addText() {
          alert("Content coming soon!");
          this.modules.push({module: "Text"});
    },
    remove(id) {
      if(confirm("Are you sure you want to delete this module?"))
      {
          this.modules.splice(id,1);
      }
    },
    editModule() {
      alert("Content coming soon!");
    },
    viewModule() {
      alert("Content coming soon!");
    },
    submitCourse() {
      alert("Content coming soon!");
    },
    viewCourse() {
      alert("Content coming soon!");
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css";

  .holder {
    background: #fff;
  }

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }

  ul li {
    padding: 20px;
    font-size: 1.3em;
    background-color: #98FB98;
    border-left: 5px solid black;
    margin-bottom: 2px;
    color: #3E5252;
  }

  p {
    text-align:center;
    padding: 20px 0;
    color: gray;
  }

  .container {
    box-shadow: 0px 0px 40px lightgray;
  }

  input {
    width: calc(100% - 40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    background-color: #323333;
    color: #687F7F;
  }
  .alert {
    background: #fdf2ce;
    font-weight: bold;
    display: inline-block;
    padding: 5px;
    margin-top: -20px;
  }

  .alert-in-enter-active {
    animation: bounce-in .5s;
  }
  .alert-in-leave-active {
    animation: bounce-in .5s reverse;
  }

@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}

i {
  float:right;
  margin-left: 20px;
  cursor:pointer;
}

button {
   background-color: primary;
   width: 10em;
   color: white;
   text-align: center;
   display: inline-block;
   font-size: 15px;
   cursor: pointer;
}
</style>
