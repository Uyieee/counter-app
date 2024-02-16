<template>
    <!-- content :  display counter-->
    <div class="counter-display">
        <!-- basic increment -->
        <div class="basic">
            <h2>Basic Count</h2>
            <h2>Number : {{ count }}</h2>
        </div>
        <!-- double increment -->
        <div class="double">
            <h2>Double Count</h2>
            <h2>Number : {{ doubleCount }}</h2>
        </div>
    </div>

    <!-- content : button -->
    <div class="counter-btn">
        <button @click="increment" class="increment-btn">Increment</button>
        <button @click="decrement" class="decrement-btn">Decrement</button>
    </div>
</template>

<script>
export default {
    name: 'CounterTask',
    props: {
        initial: {
            type: Number,
            default: 0,
        },
    },
    data() {
        return {
            count: this.initial,
        };
    },
    computed: {
        //computed for double count
        doubleCount() {
            return this.count * 2;
        },
    },
    methods: {
        //+ and - fx
        increment() {
            this.count++;
        },
        decrement() {
            this.count--;
        }
    },
    watch: {
        //alert : everytime hit multiply of 5
        count(newValue) {
        if (newValue % 5 === 0 && newValue != 0) {
            alert("Alert! The counter reached multiply of 5")

            //emit when counter hit multiply of 5
            this.$emit('count-multiple-of-five', {
                count: this.count,
                doubleCount: this.doubleCount
            });
        }
    },
        //2 way binding : user input dgn basic count & dbl count
        initial(newInitial) {
            this.count = newInitial;
        },
    }
};
</script>

<style scoped>
.counter-display {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px;
    margin-top: 20px;
    margin-bottom: 50px;
    overflow: hidden;
    box-sizing: border-box;
    border-radius: 10px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
    background: #d9f4fc;
}

.basic, .double {
    flex: 1;
    text-align: center;
    padding: 20px;
    margin-left: 10px;
    margin-right: 10px;
}

.counter-display:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.1);
}

button {
    padding: 15px 25px;
    font-size: 20px;
    background-color: #8447ff;
    color: #fff;
    border: none;
    border-radius: 55px;
    cursor: pointer;
    margin: 10px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
}

button:hover {
    background-color: #6a2cbb;
    transform: scale(1.05);
}

</style>