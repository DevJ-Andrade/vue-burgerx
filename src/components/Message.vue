<template>
<div class="message-container">
    
    {{ msg }}

    <!--<p>Esta é uma mensagem do sistema</p> -->
</div>

</template>

<script>
export default {
    name: "Message",
    props: {
        msg: String
    },
    data() {
        return {
            msg : "Pedido aprovado"
        }
    }
}
</script>

<style scoped>
.message-container {
    color: #004085;
    background-color: #CCE5FF;
    border: 2px solid #88DAFF;
    border-radius: 5px;
    padding: 10px;
    max-width: 400px;
    margin: 30px auto;
}

</style>