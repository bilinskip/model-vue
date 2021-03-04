<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <Inputs @add-model="addModel" />
    <div v-show="result">
       <Model :result="result">
      </div>
  </div>
</template>

<script>
import Inputs from './Inputs'
import Model from './Model'
export default {
  name: 'Main',
  props: {
    msg: String
  },
  data() {
    return {
         result: '',
         model: [],
         sheetLong: '',
         sheetWidth: '',
         sheetArea: '',
         ruleLenght: '',
         blankSizeInX: '',
         blankSizeInY: ''
    }
  },
  methods: {
    addModel(modelDimensions) {
      console.log('wymiary ',modelDimensions);
      this.model = modelDimensions;
     // this.result = modelDimensions.height * modelDimensions.width;
     this.createModel();
    },
    createModel(){
      if ( this.model.designType == 'fefco 200'){
        const modelLong = this.model.long;
        const modelWidth = this.model.width;
        const modelCardboardType = this.model.cardboardType;
        
        this.blankSizeInX = 2*modelLong + 2*modelWidth + 4*modelCardboardType +30;
        console.log('blank size in X ', this.blankSizeInX);
      }

    }
  },
  components :{
    Inputs,
    Model
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
