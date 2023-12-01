<template>
  <div>
    <h5>Data yang terakhir dimasukan</h5>
    <table class="table table-hover table-striped">
      <thead>
        <tr>
          <th>Field</th>
          <th>Value</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(value, field) in bon" :key="field">
          <td>{{ field }}</td>
          <td>{{ value }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
        bon : ''
    }
  },
  mounted(){
    this.test();
  },
  methods:{
    test() {
     const test = JSON.parse(localStorage.getItem('submittedData')); 
      this.bon = test; 
      console.log('submittedData in PreviewTable:', JSON.parse(localStorage.getItem('submittedData')));
    },
  }
};
</script>
