<template>
  <section>
    <h2>Crashes list</h2>
    <ul class="table-ul">
      <li v-for="(item, i) in crashTypes" :key="i">
        <ul>
          <h3>{{i}}</h3>
          <li v-for="(elem, e) in item" :key="e">Device: {{elem}}</li>
        </ul>
      </li>
    </ul>
  </section>
</template>

<script>
  export default {
    data() {
      return {
        data: [],
        crashTypes: {}
      }
    },
    beforeMount () {
      fetch('https://raw.githubusercontent.com/ok-webdev/fakeserver-db/main/db.json')
        .then(response => response.json())
        .then(data => {
          this.data = {...data};
          for (let item in this.data) {
            for(let key in this.data[item]) {
              if (this.crashTypes.hasOwnProperty === key) {
                continue;
              } else {
                this.crashTypes[key] = [];
              }
            }
          }
          for (let crash in this.crashTypes) {
            for(let item in this.data) {
              if(Object.prototype.hasOwnProperty.call(this.data[item], crash)) {
                if (this.data[item][crash].desc) {
                  this.crashTypes[crash].push(`${item}  (${this.data[item][crash].desc})`);
                } else {
                  this.crashTypes[crash].push(item);
                }
              }
            }
          }
        });
    }
  }

</script>

<style scoped>
  h2{
    margin-top: 1rem;
  }
  ul {
    list-style: none;
  }
  .table-ul{
    width: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 16px;
    color: #000;
    margin: 5% auto;
  }
  .table-ul h3 {
    margin-bottom: 0.5rem;
  }
  .table-ul li {
    margin: 0 1rem;
  }
</style>
