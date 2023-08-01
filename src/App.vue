<script>
import Products from './views/products.vue'

export default {
  data() {
    return {
      username: ''
    };
  },
  created() {
    fetch('https://randommer.io/username-generator?culture=en_US', {
      method: 'POST'
    })
  .then(response => response.json())
  .then(data => {
    var usernames = data;
    var i = 0;
    while (i < usernames.length) {
      if (usernames[i].length < 5) {
        console.log("Username is too short");
      } else if (usernames[i].length < 15) {
        console.log("Username is still not sufficient length");
      }

      else {
        console.log("Username is ideal length");
        this.username = usernames[i];
        break;
      }
      i++;
    }
      });

    // refresh the username every 5 seconds
    setTimeout(() => {
      fetch('https://randommer.io/username-generator?culture=en_US', {
        method: 'POST'
      })
  .then(response => response.json())
  .then(data => {
    var usernames = data;
    var i = 0;
    while (i < usernames.length) {
      if (usernames[i].length < 5) {
        console.log("Username is too short");
      } else if (usernames[i].length < 15) {
        console.log("Username is still not sufficient length");
      }

      else {
        console.log("Username is ideal length");
        this.username = usernames[i];
        break;
      }
      i++;
    }
  });
    }, 5000);



  },
  components: { Products }
}
</script>

<template>
  <div class="card" style="margin-right: 1.5rem">
    Welcome, {{ username }}
  </div>

  <Products />
</template>

<style>
.card {
  background-color: #747474;
  border-radius: 2px;
  display: inline-block;
  height: 250px;
  margin: 1rem;
  position: relative;
  width: 500px;
  box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.14),
    0 1px 5px 0 rgba(0, 0, 0, 0.12), 0 3px 1px -2px rgba(0, 0, 0, 0.2);
}
</style>
