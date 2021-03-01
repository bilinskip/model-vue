<template>
  <form @submit="onSubmit" class="add-form">
  <div class="form-control">
    <label> Height</label>
    <input type="number" v-model="height" name="height">
  </div>
  <div class="form-control">
    <label>Weight</label>
    <input type="number" v-model="weight" name="weight">
    <input type="submit" value="Submit"/>
  </form>
</template>

<script>
export default {
  name: 'Inputs',
  data() {
    return {
      height: '',
      weight: '',
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()

      if (!this.height){
        alert('Alert');
        return;
      }
      const modelDimensions = {
        height: this.height,
        weight: this.weight
      };
      
      this.$emit('add-model', modelDimensions);
      this.height = '';
      this.weight = '';
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
</style>
