<template>
  <div
    class="user__link"
    :style="{
      borderColor: linkBorderColor,
      backgroundColor: linkBackGroundColor,
    }"
    :href="ulink.link"
    >
    {{ ulink.text }} {{ userInfo.linkBorderColor }}
    <user-delete-button></user-delete-button>
    </div>
</template>
<script>
import { ref, toRef } from "@vue/reactivity";
import UserDeleteButton from './UserDeleteButton.vue';
export default {
  components: { UserDeleteButton },
  name: "UserLink",
  props: ["ulink","userInfo"],
  setup(props) {
    const linkBorderColor = ref("#fff");
    const linkBackGroundColor = ref("#000");

    const userInfoS = toRef(props,"userInfo");
 
    linkBorderColor.value = userInfoS.value[0].linkBorderColor;
    linkBackGroundColor.value = userInfoS.value[0].linkBackGroundColor;

    return { linkBorderColor, linkBackGroundColor };
  },
};
</script>
<style  scoped>
.user__link {
  border: solid 1px;
}
</style>