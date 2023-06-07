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
        
            <button class="btn" v-if="question" @click="handleNext">
                Next
            </button>
            <!-- mb-3 signifie margin-bottom: 3; -->
            <div v-if="error" class="error">
                You question is to short
            </div>
        </div>
        
    </div>
</template>
 
 <script>
  export default {

    data(){

        return {
            question:'',
            error:false
        }
    },
    methods:{
        handleNext(e){
            e.preventDefault();

            if(this.question.length <= 5){
                this.error = true;
            } else {
                this.error = false;
                this.$emit('goto',1);
                this.$emit('question',this.question)
            }


        }
    
    }
  }
 </script>