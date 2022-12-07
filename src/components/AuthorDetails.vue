<template>
    <div class="Author">
        <p id = "name">{{name}}</p>
        <p><a  href="https://hospital-details-by-us-state-tvt.cyclic.app/about"> About Me </a></p>
    </div>
</template>

<script>
export default{
    name:"AuthorDetails",
    data() {
      return {
        name : "Venkata Teja Thokala"
      }
    },
}

</script>

<style scoped>
.Author {
    display: inline-flex;
}
#name {
    color : blueviolet;
    font-size: 18px;
    font-weight: bolder;
    margin-left: 40px;
    margin-right: 40px;
}

a{
    text-decoration: none;
    color: blueviolet;
    font-size: 17px;
    font-weight: bolder;
}
</style>

