<template>
 <mdb-container fluid>
    <!-- Content here -->
     <mdb-row class="text-left">
        <mdb-col col="12">
          <div id="top" class="text-left">
            <mdb-navbar position="top" dark color="indigo" scrolling>
              <mdb-navbar-brand href="#">Solving Quadratic Equations</mdb-navbar-brand>
              <mdb-navbar-toggler>
                <mdb-navbar-nav right>
                  <mdb-nav-item href="#top" waves-fixed>Home</mdb-nav-item>
                  <mdb-nav-item href="#introd" waves-fixed>Introduction</mdb-nav-item>
                  <mdb-nav-item href="#ex" waves-fixed>Examples</mdb-nav-item>
                  <mdb-nav-item href="#exer" waves-fixed>Exercises</mdb-nav-item>
                </mdb-navbar-nav>
                <form>
                  <mdb-input
                    type="text"
                    class="text-white"
                    placeholder="Search"
                    aria-label="Search"
                    label
                    navInput
                    waves
                    waves-fixed
                  />
                </form>
              </mdb-navbar-toggler>
            </mdb-navbar>
            <h1 class="h1 h1-responsive text-uppercase text-center text-danger">
              Completing the Square
            </h1>
            <div id="introd" class="note note-primary">
              <h4 class="h4 h4-responsive text-primary">Introduction</h4>
              <p class="m-5">We can complete the square to solve a Quadratic Equation (find where it is equal to zero). </p>
              <p class="m-5">But a general Quadratic Equation can have a coefficient of  <span v-katex="'a'"></span>  in front of <span v-katex="'x^2' "></span></p>
              <div v-katex:display="'x^2 + bx + c = 0'"></div>
              <p class="m-5"> But that is easy to deal with ... just divide the whole equation by <span v-katex="'a'"></span> first, then carry on: 
              </p>
              <div v-katex:display="'x^2 + \\frac{b}{a}x + \\frac{c}{a} = 0'"></div>
              <div class="note note-secondary">
                <h4 class="h4-responsive h4 text-info">Steps</h4> 
                <p class="text-primary">
                  Now we can solve a Quadratic Equation in 5 steps:
                </p>
                <dl class="row">
                  <dt class="col-sm-1">Step 1</dt>
                  <dd  dd class="col-sm-11">Divide all terms by <span v-katex="'a'"></span> (the coefficient of <span v-katex="'x^2'"></span>).</dd>
                  <dt class="col-sm-1">Step 2</dt>
                  <dd  dd class="col-sm-11">Move the number term (<span v-katex="'\\frac{c}{a}'"></span>) to the right side of the equation.</dd>
                  <dt class="col-sm-1">Step 3</dt>
                  <dd  dd class="col-sm-11">Complete the square on the left side of the equation and
                  balance this by adding the same value to the right side of the equation.
                  </dd>
                </dl>
                <p class="text-primary">We now have something that looks like <span v-katex="'(x+p)^2 = q'"></span> 
                which can be solved rather easily:</p>
                <dl class="row">
                  <dt  dt class="col-sm-1">Step 4</dt>
                  <dd  dd class="col-sm-11">Take the square root on both sides of the equation.</dd>
                  <dt class="col-sm-1">Step 5</dt>
                  <dd  dd class="col-sm-11">Subtract the number thah remains on the left side of the equation to find <span v-katex="'x'"></span>.</dd>
                </dl>
              </div>     
            </div>
            <div class="note note-info mt-4" id="ex">    
              <div class="m-4">
                <h4 class="h4-responsive text-primary h4">Example</h4> 
                <p class="text-success">Use the method of completing the square to solve the 
                following quadratic equation:</p>
                  <div v-katex:display="question"></div>
                    <div v-show="answerDisplay.visibility">
                        <hr />
                      <h4 class="h4-responsive text-danger">Answer</h4>
                      <div v-katex:display="answer"></div>
                    </div>
                    <div class="container" v-show="workingDisplay.visibility">
                      <hr/>
                      <h4 class="h4-responsive text-danger">Working</h4>
                      <div class="container"> 
                          <ol class="list-unstyled"> 
                            <div class="container d-flex flex-row" v-for="working in this.working" :key="working" align="center" > 
                              <li class="flex-col"  v-katex:display="working"></li> 
                            </div> 
                          </ol> 
                      </div> 
                    </div>  
                    <!-- Default switch -->
                    <div class="custom-control custom-switch">
                      <input 
                        type="checkbox" 
                        class="custom-control-input" 
                        id="answerSwitch"  
                        v-model="answerDisplay.visibility"
                      />
                      <label class="custom-control-label" for="answerSwitch">Answer</label>
                    </div>
                    <div class="custom-control custom-switch">
                      <input 
                        type="checkbox" 
                        id="workingSwitch"
                        v-model="workingDisplay.visibility"
                        class="custom-control-input"/>
                        <label for="workingSwitch" class="custom-control-label">Working</label>
                    </div>
                <mdb-row class="mt-4"> 
                    <mdb-btn @click.native="handleClickNewExample" color="primary">
                      NEW EXAMPLE <mdb-icon icon="redo" class="ml-2"/>
                    </mdb-btn>
                </mdb-row>
              </div> 
            </div>
            <section class="preview mt-2 mb-2 text-left note note-light" id="exer">
              <div class="container">
                <div class="row">
                  <div class="col-sm-6">
                    <h4 class="h4-responsive text-primary text-left h4">Exercises</h4> 
                    <ol class="list-unstyled">
                      <div  v-for="exercise in exercises" :key="exercise" align="left">
                        <li v-katex="exercise[0]"></li>
                      </div>
                    </ol>
                  </div>
                  <div class="col-sm-6">
                    <div v-show="exerciseAnswer.visibility">
                      <h4 class="h4-responsive text-primary text-left"><strong>Answers</strong></h4> 
                      <ol class="list-unstyled">
                          <div v-for="exercise in exercises" :key="exercise" align="left" >
                          <li li v-katex="exercise[1]"></li>
                          </div>
                      </ol>
                    </div>
                  </div>
                </div>
              </div>  
              <mdb-row class="mt-2">
                <div class="custom-control custom-switch ml-4">
                  <input 
                    type="checkbox" 
                    class="custom-control-input" 
                    id="exerciseAnswerSwitch"  
                    v-model="exerciseAnswer.visibility"
                  />
                  <label class="custom-control-label" for="exerciseAnswerSwitch">Answers</label>
                </div>
              </mdb-row> 
              <mdb-row class="mt-2"> 
                <mdb-btn @click.native="handleClickNewExercises" color="primary" class="ml-4">
                  NEW EXERCISES <mdb-icon icon="redo" />
                </mdb-btn>
              </mdb-row>
            </section>
            <footer id="footer" class="page-footer font-small blue">
              <div class="footer-copyright text-center py-3">© 2020 Copyright: Siyabonga Msibi
              </div>
            </footer>
          </div>
        </mdb-col>
      </mdb-row>
  </mdb-container>
</template>
  
<script>
  import 'katex/dist/katex.min.css';
import katex from 'katex/dist/katex.mjs'
  import {
    mdbIcon,
    mdbNavbar,
    mdbNavItem,
    mdbNavbarNav,
    mdbNavbarToggler,
    mdbInput,
    mdbNavbarBrand,
    mdbBtn 
  } from "mdbvue";
  export default {
    name: "NavigationPage",
    components: {
      mdbNavbar,
      mdbNavItem,
      mdbNavbarNav,
      mdbNavbarToggler,
      mdbInput,
      mdbNavbarBrand,
      mdbBtn,
      mdbIcon
    },
    data() {
      return {
        active: false,
        answer: undefined,
        question: undefined,
        min:-9,
        max: 9,
        exercises: [],
        nExercises: 10,
        answerDisplay: {visibility: false },
        exerciseAnswer:{visibility:false},
        workingDisplay:{visibilty:false}
      };
    },
    beforeMount(){
      let temp = this.equationText(this.min,this.max)
      this.question = temp[0];
      this.answer = temp[1];
      this.exercises = this.generateExercises(this.nExercises);
    },
    methods:{
     toggleActiveState() {
         this.active = !this.active;
      },
     //function for formating 1x or -1x to be  + x or  - x
      plusOrMinus(nn) {
        let str = ' ';
        if (nn === 1){
          str = ` + `;
        }
        else if (nn=== -1) {
          str = ` - `;
        }
        else if (nn > 0){
          str = ` + ` + Math.abs(nn);
        } else {
          str = ` - ` + Math.abs(nn); 
        }
        return str
      },
      // Generate a range of numbers between start and end
      myRange(start, end) {
        let ans = [];
        for (let i = start; i <= end; i++) {
          if (i == 0){
          continue
          }
          ans.push(i);
        }
        return ans;
      },
      // Generate randomInteger between min and max 
      generateRandomInteger(min, max) {
       return Math.floor(min + Math.random()*(max + 1 - min)) 
      },
      // pick one number from a list 
      randomChoice(arr){
        let len = arr.length;
        //pos  = random position on the array 
        let pos = this.generateRandomInteger(0,len-1);
        return arr[pos]   
      },
      // generate equation with smallest root = min and largest root = max
      equationText(min,max){
        let array1 =  this.myRange(min,max);
        let array2 =  this.myRange(min,max);
        //equations  (x+b1)(x+c1)
        let b1 = this.randomChoice(array1);
        let c1 = this.randomChoice(array2);
        //avoid cases where b1 = -c1;
        if(b1 == -c1){
          if(b1 == -1){
          c1 = -b1 - 1;
          }else {
            c1 = b1 + 1
          }
        }
          
        let b = b1 + c1;
        let c = b1*c1;
        let ans = `x = ` + b1 + `\\quad \\textrm{and}  \\quad x = ` + c1 
        let eqn = ``;
        eqn = `x^2 ` + this.plusOrMinus(b) + `x  ` + this.plusOrMinus(c) + ` = 0`;

        return [eqn,ans]
      },
           createWorking(a, b, c){
       var q = (-1*c/parseFloat(a)) + (b/(2*parseFloat(a)))*(b/(2*parseFloat(a)));
       var p = (b/(2*parseFloat(a))); 
       var ans1 = Math.sqrt(q) -  p; 
       var ans2 = -1*Math.sqrt(q) - p; 
       var strB_A;
       var strB_A_r; 
       var strC_A; 
       var strC_A_r;  
       var strQ; 
       var strp; 
       q = q.toFixed(2); 
       p = p.toFixed(2); 

       if(p > 0){
         strp = ` + ` + p; 
         }
         else if(p == 0){
           strp = ``; 
         }else{
           strp = ` - ` + p; 
         }

       if((a < 0 && b < 0) || (a > 0 && b > 0)) {
         strB_A = ` + \\frac{`+Math.abs(b)+`}{ ` + Math.abs(a) + `}`;          
         strB_A_r = ` - \\frac{`+Math.abs(b)+`}{ ` + Math.abs(a) + `}`;          
       }else{
         strB_A = ` - \\frac{`+Math.abs(b)+`}{ ` + Math.abs(a) + `}`;          
         strB_A_r = ` + \\frac{`+Math.abs(b)+`}{ ` + Math.abs(a) + `}`;          

       }

       if((a < 0 && c < 0) || (a > 0 && c > 0)) {
         strC_A = ` + \\frac{`+Math.abs(c)+`}{` + Math.abs(a) + `}`;          
         strC_A_r = ` - \\frac{`+Math.abs(c)+`}{` + Math.abs(a) + `}`;          
       }else{
         strC_A = ` - \\frac{`+Math.abs(c)+`}{` + Math.abs(a) + `}`;          
         strC_A_r = ` \\frac{`+Math.abs(c)+`}{` + Math.abs(a) + `}`;          

       }
        strQ = strC_A_r + strB_A_r + ` \\times \\frac{1}{2}`; 

       //var workingStep1 = `x^2 + \\frac{` + b`}{`+ a +`}x + \\frac{`+ c +`}{`+ a +`} = 0`; 
       var workingStep1 = `x^2` + strB_A + strC_A + ` = 0`; 
       //var workingStep2 = `x^2 + \\frac{` + b`}{`+ a +`}x  = \\frac{`+ c +`}{`+ a +`} ` ; 
       var workingStep2 = `x^2` + strB_A + ` =` + strC_A_r; 
       //var workingStep3 = `(x + \\frac{` + b`}{`+ a +`})^2  = ` + q;  
       var workingStep3 = `(x`+ strB_A + ` \\times \\frac{1}{2})^2 =` + strQ; 
       var workingStep4 = `(x ` + strp + ` )^2 = `+q;
       var workingStep5 = `\\sqrt{(x ` + strp + ` )^2} = \\sqrt{`+q+`}`;

       var workingAnswer  = `x = ` + ans1.toFixed(2) + `\\quad \\textrm{and}  \\quad x = ` + ans2.toFixed(2);  
       workingAnswer = this.answer; 
       let set = []; 
       set.push(workingStep1); 
       set.push(workingStep2); 
       set.push(workingStep3); 
       set.push(workingStep4); 
       set.push(workingStep5); 
       set.push(workingAnswer); 

       this.working = set; 
       return set; 
       },
      generateExercises(n){
        let set = [];
        for(let i = 0; i < n-1;i++){
          set.push(this.equationText(this.min,this.max))
        }
        this.exercises = set;
        return set;
      },
      handleClickNewExample() {
        let temp = this.equationText(this.min,this.max)
        this.question = temp[0];
        this.answer = temp[1];
        this.update_element('question', this.question);
        this.update_element('answer', this.answer);
        this.update_element('working', this.Working);
      },
      handleClickNewExercises() {
        this.exercises = this.generateExercises(this.nExercises);
        this.update_element('exercises', this.exercises);
      },
      update_element(element, value){
        // eslint-disable-next-line no-undef
        katex.render(value, this.$refs[`${element}`], {
          throwOnError: false
        });
      },
      showAnswerDsiplay() {
        this.answerDisplay.visibility = true;
      },
      showExericesAnswers() {
        this.exerciseAnswer.visibility = true;
      },
      showWorkingDisplay(){
        this.workingDisplay.visibility = true;
      }
    },
  }
</script>
<style scoped>
  .view {
    background: #4169E1
      no-repeat center center;
    background-size: cover;
    height: 100%;
  }

  .navbar .dropdown-menu a:hover {
    color: inherit !important;
  }

  li{
    align-items: left;
  }

  .note {
  padding: 10px;
  border-left: 6px solid;
  -webkit-border-radius: 5px;
  border-radius: 5px; 
  }
  .note strong {
    font-weight: 600; 
  }
  .note p {
    font-weight: 500; 
  }
  .note.note-primary {
    background-color: #dfeefd;
    border-color: #176ac4; 
  }
  .note.note-secondary {
    background-color: #e2e3e5;
    border-color: #58595a; 
  }
  .note.note-success {
    background-color: #e2f0e5;
    border-color: #49a75f; 
  }
  .note.note-danger {
    background-color: #fae7e8;
    border-color: #e45460; 
  }
  .note.note-warning {
    background-color: #faf4e0;
    border-color: #c2a442; 
  }
  .note.note-info {
    background-color: #e4f2f5;
    border-color: #2492a5; 
  }
  .note.note-light {
    background-color: #fefefe;
    border-color: #0f0f0f; 
  }
</style>