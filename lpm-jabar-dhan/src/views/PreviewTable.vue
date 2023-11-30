<template>
  <div>
    <h5>Preview Data</h5>
    <pre>{{ submittedData }}</pre>
    <!-- Rest of the component -->
  </div>
</template>

<script>
export default {
  props: {
    submittedData: Object,
  },
  mounted(){
    this.test();
  },
  methods:{
    test(){
      alert('test');
    console.log(this.submittedData)

    }
  }
};
</script>
