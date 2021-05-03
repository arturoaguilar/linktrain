<template>
  <!--<div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />

  </div>-->

<User-links-list></User-links-list>
</template>

<script>
// @ is an alias to /src

import UserLinksList from '../components/user/UserLinksList.vue' ;

export default {
  name: "Home",
  components: {

    UserLinksList,
  },
};
</script>
