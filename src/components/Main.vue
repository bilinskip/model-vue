<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <Inputs @add-model="addModel" />
    <div v-show="ruleLength">
       <Model :area="sheetArea" :ruleLength="ruleLength" :sheetSize="sheetSize">
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
         ruleLength: '',
         blankSizeInX: '',
         blankSizeInY: '',
         sheetSize: ''
    }
  },
  methods: {
    addModel(modelDimensions) {
      console.log('wymiary ',modelDimensions);
      this.model = modelDimensions;
     this.createModel();
    },
    createModel(){
      if (this.model.designType == 'fefco 200'){
        const modelLong = this.model.long;
        const modelWidth = this.model.width;
        const modelHeight = this.model.height;
        const modelCardboardType = this.model.cardboardType;
    
        this.blankSizeInX = 2*modelLong + 2*modelWidth + 4*modelCardboardType +30;
        this.blankSizeInY = 1*modelHeight + modelWidth/2 + ((3/2)*modelCardboardType);
        this.sheetSize =`sheet size: ${this.blankSizeInY}x${this.blankSizeInX}`;
        this.sheetArea = (this.blankSizeInX * this.blankSizeInY) / 1000000;

        this.ruleLength = (6*modelLong + 10*modelWidth + 22*modelCardboardType + 6*modelHeight + 60) / 1000;
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
