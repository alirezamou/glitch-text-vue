<template>
    <p>{{ displayText }}</p>
    <button @click="displayText += displayText">Click</button>
</template>

<script>
export default {
    props: {
        text: String,
    },
    data() {
        return {
            displayText: "",
            target: "",
            randomChars: "~!@#$%^&*()<>/",
        }
    },
    methods: {
        updateDisplay () {
            if(this.target.length < this.text.length) {
                let tempText = this.target + this.text[this.target.length];
                tempText += this.glitchChar();
                this.target += this.text[this.target.length];
                console.log(this.target);
                this.displayText = tempText;
                setTimeout(() => this.updateDisplay(), 100);
            } else {
                this.displayText = this.text;
            }
        },
        glitchChar() {
            const r = Math.ceil(Math.random() * 10) % this.text.length;
            return this.randomChars[r];
        }
    },
    mounted() {
        this.updateDisplay("");
    },
    watch: {
        displayText: {
            handler(val) {
                // console.log("under watch, val is: ", val)
            }
        }
    }
}
</script>