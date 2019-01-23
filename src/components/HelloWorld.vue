<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button @click="run_xHTTPRequest">XHTTPRequest</button>
    <button @click="run_axios">Axios</button>
  </div>
</template>

<script>
import { axios } from 'axios'


export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "Welcome to Your Vue.js App"
    };
  },
  methods: {
    run_axios: function() {
      const url="https://ussouthcentral.services.azureml.net/workspaces/8a9e6c2473674cbda1a9047e2e1258e2/services/0729753e4be646f3b0e1e0079df19ee8/execute?api-version=2.0&details=true"
      const auth="Bearer taYapadAQL5Ho5uaHZQI0xugDVHJTl0C3/5XahbZKPiUGYYptmfwAMQB8pGqJuIP+RwZcnR/7n30QDBJ54Vk+Q==";
      const data = { "Inputs": { "input1": {
        "ColumnNames": ["Indice", "Nivel", "G_conta", "NumCta", "Desc", "CodAgrup", "DescAgrup"],
        "Values": [
          ["1", "1", "Capital", "101", "Banco", "value1", "value2" ],
          ["2", "2", "Capital", "102", "Caja", "", "value2" ],
          ["3", "2", "Capital", "102", "Caja", "value1", "value2" ],
        ]
        }},
        "GlobalParameters": {}
      }
      const json = JSON.stringify(data);

      var config = {
        headers: {
          "Content-type": "application/json",
          "Authorization": auth,
        }
      };

      axios.post(url, data, config)
        .then(function(response){
          alert("THEN:" + response);
        })
        .catch(function(error){
          alert("ERROR:" + response);
        });
      
    },
    run_xHTTPRequest: function() {
      const url="https://ussouthcentral.services.azureml.net/workspaces/8a9e6c2473674cbda1a9047e2e1258e2/services/0729753e4be646f3b0e1e0079df19ee8/execute?api-version=2.0&details=true";
      const auth="Bearer taYapadAQL5Ho5uaHZQI0xugDVHJTl0C3/5XahbZKPiUGYYptmfwAMQB8pGqJuIP+RwZcnR/7n30QDBJ54Vk+Q==";
      const data = { "Inputs": { "input1": {
        "ColumnNames": ["Indice", "Nivel", "G_conta", "NumCta", "Desc", "CodAgrup", "DescAgrup"],
        "Values": [
          ["1", "1", "Capital", "101", "Banco", "value1", "value2" ],
          ["2", "2", "Capital", "102", "Caja", "", "value2" ],
          ["3", "2", "Capital", "102", "Caja", "value1", "value2" ],
        ]
        }},
        "GlobalParameters": {}
      }

      const json = JSON.stringify(data);
      
      alert("prepare");
      
      var xhttp = new XMLHttpRequest();
      xhttp.onreadystatechange = function() {
        alert("Change:" + xhttp.readyState + " - " + xhttp.status + " [" + xhttp.responseText + "]");
      };
      xhttp.onprogress = function() {
        alert("Progress:" + xhttp.readyState + " - " + xhttp.status + " [" + xhttp.responseText + "]");
      };
      xhttp.onload = function() {
        alert("Load:" + xhttp.readyState + " - " + xhttp.status + " [" + xhttp.responseText + "]");
      };
      xhttp.onerror = function() {
        alert("OnError:" + xhttp.readyState + " - " + xhttp.status + " [" + xhttp.responseText + "]");
        alert("Error: " + xhttp.error)
      };

      xhttp.open("POST", url, true);
      xhttp.setRequestHeader("Content-type", "application/json");
      xhttp.setRequestHeader("Authorization", auth);
      xhttp.send(data);
      
      alert("sent");

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
