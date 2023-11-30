<template>
  <div>
    <h1>This is the Preview Page</h1>
    <!-- <router-view :submittedData="submittedData" v-if="showPreview" /> -->
  </div>
</template>

<script>
export default {
  props: {
    submittedData: Object,
  },
  mounted() {
    this.test();
  },
  methods: {
    test() {
      console.log('submittedData in PreviewTable:', this.submittedData);
    },
  },
};
</script>