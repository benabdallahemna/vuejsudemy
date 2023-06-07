<template>

<div class="container">
  <component
        :is="screens[position]"
        :question="question"
        @goto="handleGoTo"
        @question="handleQuestion"
      />
</div>

<!-- :is pour seletioner une component de maniere dynamic -->
</template>
  
  <script>
   import appInitial from './components/AppInitial.vue'
   import appConfirm from './components/AppConfirm.vue';
   import appResults from './components/AppResults.vue';
  
   export default {
     components:{
       appInitial,
       appConfirm,
       appResults
     },

     data()
    {
        return{
          screens:['appInitial','appConfirm','appResults'],
          position:0,
          question:''
        }
    },
    methods:{
     handleGoTo(position){
       this.position = position
     },
     handleQuestion(question){
       this.question = question
     }
   }
   }

   
  </script>
  
  <style>
    @import './assets/style.css';
  
  </style>