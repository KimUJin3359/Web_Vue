<template>
  <div>
    <button v-on:click="getData">버튼</button>
    <ol>
      <li></li>
    </ol>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  methods: {
    async getData() {
      try {
        const { data } = await this.$http.get("https://koreanjson.com/users");
        const ol = document.querySelector('ol');
        console.log(data);
        for (let i = 0; i < data.length; i++) {
          const li = document.createElement("li");
          li.innerHTML = "이름 : " + data[i].name + 
          ", 전화번호 : " + data[i].phone + ", 사는 곳 : " + data[i].province + " " + data[i].city ;
          ol.append(li);
        }
      } catch (error) {
        console.log(error);
      }
    },
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
