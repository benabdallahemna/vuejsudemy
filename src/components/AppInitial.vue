<template>
    <div>
        <h1>Ask a question </h1>
        <div class="mb-3"> 
            <input
                name="question"
                type="text"
                class="form-control"
                id="question"
                v-model="question"
            />
            <!-- v-model="question" Vue.js écoute les événements de saisie de l'utilisateur sur 
            l'élément et met à jour automatiquement la valeur de la propriété question  -->
        
            <button class="btn  animate__animated animate__fadeIn" 
            v-if="question" 
            @click="handleNext">
                Next
            </button>
            <!-- mb-3 signifie margin-bottom: 3; -->
            <!-- <div v-if="error" class="error">
                You question is to short
            </div> -->
        </div>
        
    </div>
</template>
 
 <script>
  export default {

    data(){

        return {
            question:'',
            // error:false
        }
    },
    methods:{
        handleNext(e){
            e.preventDefault();

            if(this.question.length <= 5){
                // this.error = true;
                this.$emit('handleToast',{
                    type:'error',
                    message:`You question is to short`
                })
            }  else if(this.question.length >= 50){
                this.$emit('handleToast',{
                    type:'error',
                    message:`You question is to long`
                })
            }else {
                this.error = false;
                this.$emit('goto',1);
                this.$emit('question',this.question)
            }


        }
    
    }
  }
 </script>