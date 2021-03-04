<template>
  <div>
    <p> Area is {{area}}</p>
    <p> Rule Length is {{ruleLength}}</p>
    <p> {{sheetSize}}</p>
  </div>
</template>

<script>
export default {
  name: 'Model',
  props: {
    area: Number,
    ruleLength: Number,
    sheetSize: String
  }
}
</script>
<style scoped>
  
</style>