<template>
  <div class="model-div">
    <p>Area is {{sheetArea}}</p>
    <p>Rule Length is {{ruleLength}}</p>
    <p>{{sheetSize}}</p>
  </div>
</template>

<script>
export default {
  name: 'Model',
  props: {
    model: {
      long: Number,
      width: Number,
      height: Number,
      cardboardType: Number,
      designType: String
    }
  },
  data(){
      return {
         ruleLength: '',
         blankSizeInX: '',
         blankSizeInY: '',
         sheetSize: '',
         sheetArea: '',
         FEFCO200: 'fefco 200',
         FEFCO201: 'fefco 201'
      }
  },
  watch: {
    model: function(){
      this.createModel();
    }
  },
  methods: {
    createModel(){
      console.log('this.model.designType', this.model.designType);
      if (this.model.designType == this.FEFCO200){
        this.createFefco200(this.model);
      }
      else if (this.model.designType === this.FEFCO201){
        this.createFefco201(this.model);

      }
    },
    createFefco200(model){
      console.log('model in fefco 200 ', model);
      this.blankSizeInX = 2*model.long + 2*model.width + 4*model.cardboardType +30;
      this.blankSizeInY = model.height + model.width/2 + ((3/2)*model.cardboardType);
      this.sheetSize =`sheet size: ${this.blankSizeInY}x${this.blankSizeInX}`;
      this.sheetArea = (this.blankSizeInX * this.blankSizeInY) / 1000000;
      this.ruleLength = (6*model.long + 10*model.width + 22*model.cardboardType + 6*model.height + 60) / 1000;
    },
     createFefco201(model){
      console.log('model in fefco 201 ', model);
      this.blankSizeInX = 2*model.long + 2*model.width + 2*model.cardboardType +30;
      this.blankSizeInY = model.height + model.width/2 + (model.cardboardType);
      this.sheetSize =`sheet size: ${this.blankSizeInY}x${this.blankSizeInX}`;
      this.sheetArea = (this.blankSizeInX * this.blankSizeInY) / 1000000;
      this.ruleLength = (8*model.long + 8*model.width + 20*model.cardboardType + 8*model.height + 60) / 1000;
    }
  }
}
</script>
<style scoped>
  .model-div{
    border: 2px solid black;
  }
  
</style>