<template>
  <div class="user__list">
    <!-- <user-link
      v-for="ulink in userLinks"
      :key="ulink.code"
      :ulink="ulink"
      :userInfo="userInfo"
    >
    </user-link> -->
    <user-link-edit
      v-for="ulink in userLinks"
      :key="ulink.code"
      :ulink="ulink"
      :userInfo="userInfo"
    ></user-link-edit>
  </div>
</template>
<script>
import { ref, toRef } from "@vue/reactivity";
import UserLink from "./UserLink.vue";
import UserLinkEdit from './UserLinkEdit.vue';
export default {
  components: { UserLink, UserLinkEdit },
  name: "UserLinksList",
  props: ["userName", "userInfo"],
  setup(props) {
    const userLinks = ref([]);
    
  const userName = 'arturoa';
  const newUserInfo= toRef(props,"userInfo");
    console.log("NEW USER INFO ");
    console.log(newUserInfo.value[0]);
    fetch("https://linktrainback.herokuapp.com/links/" + userName)
      .then((res) => res.json())
      .then((data) => {
        userLinks.value = data;
      });
    return {
      userLinks,
      newUserInfo
  
    };
  },
};
</script>
<style scoped >
.user__list {
  display: flex;
  flex-direction: column;
}
</style>
