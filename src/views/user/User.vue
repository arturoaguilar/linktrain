<template>
 <h1>User Admin </h1>
 <router-link to="/user/myprofile" >Admin Profile</router-link>
  <router-link to="/user/mylinks"> Admin Links</router-link>
   <router-view></router-view>
</template>
<script>

export default {
  name: "User",
  setup() {},
};
</script>
