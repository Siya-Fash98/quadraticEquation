<template> 
    <div class="note note-info mt-4" id="ex">    
              <div class="m-4">
                <h4 class="h4-responsive text-primary"><strong>Example</strong></h4> 
                <p class="text-success">Use the method of completing the square to solve the 
                following quadratic equation:</p>
                  <div v-katex:display="question"></div>
                    <div v-show="answerDisplay.visibility">
                        <hr />
                      <h4 class="h4-responsive text-danger">Answer</h4>
                      <div v-katex:display="answer"></div>
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
                <mdb-row class="mt-4"> 
                    <mdb-btn @click.native="handleClickNewExample" color="primary">
                      NEW EXAMPLE <mdb-icon icon="redo"/>
                    </mdb-btn>
                </mdb-row>
              </div> 
            </div>
</template>