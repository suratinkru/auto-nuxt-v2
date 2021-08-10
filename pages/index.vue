<template>
  <Tutorial/>
</template>

<script>
import axios from 'axios'
export default {
  mounted() {
    this.gettest();
  },
  methods: {
  async  gettest(){
      const res = await axios.get('http://localhost:2000/test');
      console.log("res:",res);
    }
  },
}
</script>
