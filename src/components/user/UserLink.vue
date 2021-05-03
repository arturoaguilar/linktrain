<template>
  <a class="user__link" :style="{ borderColor: linkBorderColor, backgroundColor:linkBackGroundColor}" :href="ulink.link">{{ ulink.text }} {{userinfo.linkBorderColor}}</a>
</template>
<script>
import { ref, toRef } from "@vue/reactivity";
export default {
  name: "UserLink",
  props: ['ulink','userinfo'],
  setup(props) {
    const linkBorderColor = ref('#fff');
    const linkBackGroundColor = ref('#000');


 const userInfoS=toRef(props, "userinfo");
 linkBorderColor.value=userInfoS.value[0].linkBorderColor;
 linkBackGroundColor.value =userInfoS.value[0].linkBackGroundColor;

return {linkBorderColor,linkBackGroundColor}
  },
};
</script>
<style  scoped>
.user__link {
  border: solid 1px;
}
</style>