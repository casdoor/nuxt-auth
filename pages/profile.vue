// Copyright 2024 The Casdoor Authors. All Rights Reserved.
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at
//
//      http://www.apache.org/licenses/LICENSE-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.

<template>
  <div>
    <h1>Hello {{ userJson.name }}!</h1>
    <hr>
    <div class="container">
      <table>
        <tbody>
        <tr>
          <td>Username</td>
          <td>{{ userJson.preferred_username }}</td>
        </tr>
        <tr>
          <td>Display Name</td>
          <td>{{ userJson.name }}</td>
        </tr>
        <tr>
          <td>User ID</td>
          <td>{{ userJson.sub }}</td>
        </tr>
        <tr>
          <td>Avatar</td>
          <td><img :src="userJson.picture" alt="Avatar"></td>
        </tr>
        </tbody>
      </table>
      <br>
      <button @click="handleLogout">Logout</button>
    </div>
  </div>
</template>

<script>
import Cookies from 'js-cookie';

export default {
  name: 'Page',
  data() {
    return {
      userJson: {}
    };
  },
  mounted() {
    const user = Cookies.get('casdoorUser');
    this.userJson = user ? JSON.parse(user) : {};
    console.log(this.userJson)
  },
  methods: {
    handleLogout() {
      Cookies.remove('casdoorUser');
      this.$router.push('/');
    }
  }
};
</script>

<style scoped>
</style>
