<script>
import axios from "axios";

export default {
  data() {
    return {
      id:0,
      title: '',
      userId: 0,
      completed: false
    }
  },
  created() {
    this.get(); // 컴포넌트가 생성될 때 데이터를 가져오도록 함
  },
  methods: {
    get: function () {
      let dataCollection = []
      axios.get('http://localhost:3000/todo')
        .then(res => {
          dataCollection = res.data
          console.log('dataCollection: ', dataCollection);
          dataCollection.forEach(data => {
            document.querySelector('.print-data').innerHTML
              += `<li>id: ${data.id} <br>title: ${data.flavor} <br> content: ${data.quantity}</li>`
          })
        })
        .catch((error) => console.log(error))
    },
  }
}
</script>

<template>
  <div id="app">
    <div class="print-data">
      <ul></ul>
    </div>
  </div>
</template>

<style>
.box-wrap {
  display: table;
  width: 100%;
  height: 30px;
  table-layout: fixed;
}

.box-wrap .box {
  display: table-cell;
  text-align: left;
  vertical-align: middle;
//border: 1px grey solid;
}
.button {
  width: 100%;
  height: 30px;
}
</style>
