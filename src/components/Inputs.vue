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
      <option v-for="option in options" v-bind:value="option.value">
    {{ option.text }}
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
      options: [
      { text: 'B', value: '3' },
      { text: 'C', value: '4' },
      { text: 'E', value: '2' }
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
        cardboardType: this.cardboardType 
      };
      
      this.$emit('add-model', modelDimensions);
      this.long = '';
      this.width = '';
      this.height = '';
    },
    setCardboardType(event){
      this.cardboardType = event.target.value;
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
}
</style>
