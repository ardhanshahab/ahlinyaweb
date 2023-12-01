<template>
  <div>
    <h4>This is the Preview Page</h4>
    <h4>Lama Loading : {{ loading }} ms</h4>
    <!-- <router-view :submittedData="bon" v-if="showPreview" /> -->
    <div class="container">
    <PreviewTable></PreviewTable>
    </div>
  </div>
</template>

<script>
import PreviewTable from './PreviewTable.vue';
export default {
  components :{
    PreviewTable,
  },
  data() {
    return {
        loading : ''
    }
  },
  mounted(){
    this.test();
  },
  methods:{
    test() {
      const storedRandomTimeoutString = localStorage.getItem('loading');
      const storedRandomTimeout = parseInt(storedRandomTimeoutString, 10);
      this.loading = storedRandomTimeout;
      console.log(storedRandomTimeout);
    },
  }
};
</script>