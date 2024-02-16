<template>
    <div class="msg-card">
        <h1>Log Message</h1>
        <!-- line between title & contents -->
        <hr>
        <!-- content : counter log msg everytime hit multiply of 5 -->
        <p v-html="logMsg"></p>
    </div>
</template>

<script>
export default {
    name: 'LoggerTask',
    props: {
        logMsg: {
            type: String,
            default: '',
        },
    },
};
</script>

<style scoped>
.msg-card {
    width: 40%;
    margin: 20px auto;
    padding: 20px;
    border-radius: 10px;
    background: #d9f4fc;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    transition: all 0.3s ease;
    margin-top: 40px;
}

.msg-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.1);
}

h1 {
    font-size: 24px;
    color: black;
}

hr {
    width: 100%;
    margin: 10px 0;
    border: 0;
    border-top: 2px solid black;
}

p {
    font-size: 25px;
    color: black;
    margin-top: 10px;
}

</style>