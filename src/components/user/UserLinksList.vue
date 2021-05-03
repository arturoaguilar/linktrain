<template>
<div class="user__list">
  <user-link v-for="ulink in userLinks" :key="ulink.code" :ulink="ulink" :userinfo="newUserInfo">
  </user-link>
</div>
</template>
<script>
import { ref,toRef } from "@vue/reactivity";
import UserLink from "./UserLink.vue";
export default {
  components: { UserLink },
  name: "UserLinksList",
  props:["userName","userinfo"],
  setup(props) {
    const userLinks = ref([]);
/*const userName= toRef(props,'userName');
console.log(props.userName);*/
  const nuserName = toRef(props, "userName");
const newUserInfo = toRef(props, "userinfo");
  console.log(nuserName.value);
    fetch("https://linktrainback.herokuapp.com/links/"+nuserName.value)
    .then(res => res.json())
    .then(data =>{
      userLinks.value = data;
    })
  return {
      userLinks,
      newUserInfo

  }
  },
};
</script>
<style scoped >
.user__list{
 display: flex;
 flex-direction: column;
}
</style>
