<template>
    <button @click="deleteThisLink()"> Delete </button>
</template>
<script>
export default {
    name:"UserDeleteLinkButton",
    setup() {
        function deleteThisLink(){
            console.log("This link have been delete");
        }
        return {deleteThisLink}
    },
}
</script>
