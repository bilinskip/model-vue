<template>
  <form @submit="onSubmit" class="add-form">
  <div class="form-control">
    <label>Long</label>
    <input type="number" v-model="long" name="long">
  </div>
  <div class="form-control">
    <label>Width</label>
    <input type="number" v-model="width" name="width">
  </div>
  <div class="form-control">
    <label> Height</label>
    <input type="number" v-model="height" name="height">
  </div>
  <div class="form-control">
    <label>Cardboard types</label>
    <select id="cardboard" v-model="carboardType" @change="setCardboardType">
      <option v-for="type in cardboardTypes" v-bind:value="type.value">
        {{ type.text }}
      </option>
    </select>
  </div>
  <div class="form-control">
    <label>Design types</label>
    <select id="design" v-model="designType" 
    @change="setDesignType">
      <option v-for="type in designTypes" v-bind:value="type.value">
        {{ type.text }}
      </option>
    </select>
  </div>
    <input type="submit" value="Submit" class="submit-class"/>
  </form>
</template>

<script>
export default {
  name: 'Inputs',
  data() {
    return {
      long: '',
      width: '',
      height: '',
      carboardType: '',
      cardboardTypes: [
      { text: 'B', value: '3' },
      { text: 'C', value: '4' },
      { text: 'E', value: '2' }
    ],
      designType: '',
      designTypes: [
      { text: 'fefco 200', value: 'fefco 200' },
      { text: 'fefco 201', value: 'fefco 201' },
      { text: 'fefco 202', value: 'fefco 202' }
    ]
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()
      const modelDimensions = {
        long: this.long,
        width: this.width,
        height: this.height,
        cardboardType: this.cardboardType,
        designType: this.designType
      };
      
      this.$emit('add-model', modelDimensions);
     /* this.long = '';
      this.width = '';
      this.height = '';
      this.cardboardType = '';
      this.designType = '';*/
    },
    setCardboardType(event){
      this.cardboardType = event.target.value;
    },
    setDesignType(event){
      this.designType = event.target.value;
    }
  }
}
</script>

<style scoped>
.form-control{
  margin: 10px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 80%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.submit-class {
  width: 80%;
  height: 60px;
  font-size: 20px;
  font-weight: 700;
}
</style>
