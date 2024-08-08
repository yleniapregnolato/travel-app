<script>
export default {

}
</script>

<template>
    <div class="container">
        <div class="row">
            <div class="col-8">
                <h2>Travel-app</h2>
                <!-- <img src="../assets/img/logo.png" alt="logo" class="logo-img"> -->
            </div>
            <div class="col-4 justify-content-between">
                <ul class="d-flex justify-content-between">
                    <li>Home</li>
                    <li>I miei viaggi</li>
                    <li>Contatti</li>
                </ul>
            </div>
        </div>
    </div>
</template>

<style scoped lang="scss">
.row {
    padding: 15px;
    color: white;
    font-size: 25px;
    background-color: var(--header-color);
    border-radius: 30px;
    background-color: rgba(0,0,0,0.1);
    .col-8, .col-4 {
        z-index: 2;
        ul {
            list-style: none;
        }
    }
}
</style>