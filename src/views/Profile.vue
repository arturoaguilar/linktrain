<template>
<main class="user__profile" :style="{ backgroundColor: profileBackColor}"> 
  <user-profile-header class="user__profile__header--container" :userinfo="userinfo"></user-profile-header>
  <user-links-list class="user__profile__body--container" :userName="userName" :userinfo="userinfo" ></user-links-list>
  <div class="user__profile__footer--container"> Powered by Arturo Aguilar</div>
</main>
</template>
<script>
import { ref, toRef } from "@vue/reactivity";
import UserLinksList from "../components/user/UserLinksList.vue";
import UserProfileHeader from "../components/user/UserProfileHeader.vue";
export default {
  components: { UserLinksList, UserProfileHeader },
  name: "Profile",
  props: ["userName"],
  setup(props) {
    const userinfo = ref([]);
    let profileBackColor = ref('');
    const nuserName = toRef(props, "userName");

    console.log(nuserName.value);
    fetch("https://linktrainback.herokuapp.com/user/" + nuserName.value)
      .then((res) => res.json())
      .then((data) => {
        userinfo.value = data;
        profileBackColor.value=data[0].backgroundColor;


      });
    return {
      userinfo,
      profileBackColor,
    };
  },
};
</script>
<style scoped>
.user__profile{
  display: grid;
  grid-template-areas: "header " "body" "footer";
  height: 100vh;
}
.user__profile__header--container{
grid-area: header;
}
.user__profile__body--container{
grid-area:body;
}
.user__profile__footer--container{
  grid-area: footer;
}
</style>