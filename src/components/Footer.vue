<template>
    <div class="footer">
        <p></p>
        <p class="name">Developer: Vajith Chamuditha</p>
        <p class="link">
            <a href="http://linkedin.com/in/vajith-chamuditha-9545b7195" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/linkedin.svg" alt="vajith-chamuditha" height="21" width="30" /></a>
            <a href="https://github.com/vajithChamuditha-99" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/github.svg" alt="vajith-chamuditha" height="24" width="30" /></a>
        </p>
    </div>
</template>

<script>
export default {
    name: "Footer"
}
</script>

<style scoped>
    .footer{
        display: flex;
        background:slateblue;
        color: #fff;
        padding: 9px;
        font-size: 15px;
        font-family: sans-serif;
    }
    .footer a{
        color: #fff;
        padding-right: 1px;
    }
    .link{
        float: right;
    }
</style>