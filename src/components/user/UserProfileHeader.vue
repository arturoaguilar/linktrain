<template>

  <div class="profile__header" v-for="user in userinfo" :key="user.name">

        <img class="profile__image" :src="user.profilePicture">
              <b>@{{ user.name }}</b>
  </div>
 
</template>
<script>
export default {
  name: "UserProfileHeader",
  props: ["userinfo"],
  setup() {

  },
};
</script>
<style scoped>
.profile__header{
    display: flex;
    flex-direction: column;
    align-items: center;

}
.profile__image{
    border-radius: 50%;
    width: 100px;
}
</style>