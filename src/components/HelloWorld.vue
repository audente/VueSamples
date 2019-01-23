<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button @click="run">Run</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "Welcome to Your Vue.js App"
    };
  },
  methods: {
    run: function() {
      const url="https://ussouthcentral.services.azureml.net/workspaces/8a9e6c2473674cbda1a9047e2e1258e2/services/28c646b4a5a449cfae71eae39c1f7302/execute?api-version=2.0&details=true";
      const auth="Bearer WBRsuaQ36vLeSR2iWDlLCB1gmPAO64N0G9vMJinQ2MWJfefqnAGFaxjWxxuL5JyqasL3VzpBHmp9QJLj3uX2Kw==";
      const data = {"Inputs": {"input1": {
        "ColumnNames": ["Indice", "NumCta", "Desc", "CodAgrup", "DescAgrup"],
        "Values": [
            ["1", "101", "Caja", "value1", "value2" ],
            ["2", "201", "Capital", "value3", "value4" ]
        ] } },
        "GlobalParameters": {}
      }
      const json = JSON.stringify(data);
      
      alert("prepare");
      
      var xhttp = new XMLHttpRequest();
      xhttp.onreadystatechange = function() {
           if (this.readyState == 4 && this.status == 200) {
               alert(this.responseText);
           } else {
             alert("FAILED:" + this.readyState + " - " + this.status + " >> " + this.responseText);
           }
      };
      xhttp.open("POST", url, true);
      xhttp.setRequestHeader("Content-type", "application/json");
      xhttp.setRequestHeader("Authorization", auth);
      xhttp.setRequestHeader("Host", "ussouthcentral.services.azureml.net");
      xhttp.send(json);
      
      alert(("sent");

    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
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
