<template>
    <div id="app">
        <div class="flex justify-between items-center w-64">
            <div>{{ firstNumber }}</div>
            <svg width="16" height="16" viewBox="0 0 16 17" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                    d="M12.6667 4.77333L11.7267 3.83333L8 7.56L4.27333 3.83333L3.33333 4.77333L7.06 8.5L3.33333 12.2267L4.27333 13.1667L8 9.44L11.7267 13.1667L12.6667 12.2267L8.94 8.5L12.6667 4.77333Z"
                    fill="black"
                />
            </svg>
            <div>{{ secondNumber }}</div>
            <div>=</div>
            <input
                class="border border-black border-opacity-10 h-10 px-3 rounded-xl w-24 appearance-none"
                type="number"
                @keyup.enter="submitAnswer()"
                placeholder="Answer"
                v-model="answer"
            />
        </div>
    </div>
</template>

<script>
import "@/assets/css/tailwind.css";

export default {
    name: "app",
    components: {},
    data() {
        return {
            firstNumber: 1,
            secondNumber: 2,
            answer: 0,
        };
    },
    methods: {
        getRandomInt(max) {
            return Math.floor(Math.random() * Math.floor(max-1)) + 1;
        },
        newNumbers() {
            this.firstNumber = this.getRandomInt(10);
            this.secondNumber = this.getRandomInt(10);
            this.answer = Number
        },
        submitAnswer(){
            if (this.answer == this.firstNumber * this.secondNumber){
                return this.newNumbers();
            }
        }
    },
    mounted() {
        this.newNumbers();
    },
};
</script>

<style lang="postcss">
#app {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial;
    font-weight: 400;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #000000;
    width: full;
    height: 100vh;

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
    /* display: none; <- Crashes Chrome on hover */
    -webkit-appearance: none;
    margin: 0; /* <-- Apparently some margin are still there even though it's hidden */
}
input:focus {
    outline: none;
}
</style>
