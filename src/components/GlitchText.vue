<template>
    <p class="glitch-text">{{ displayText }}</p>
</template>

<script>
export default {
    props: {
        text: String,
        speed: Number
    },
    data() {
        return {
            displayText: "",
            target: "",
            randomChars: "~!@#$%^&*()<>/",
            defaultSpeed: 300,
            currentSpeed: 0
        }
    },
    methods: {
        updateDisplay () {
            if(this.target.length < this.text.length) {
                let tempText = this.target + this.text[this.target.length];
                tempText += this.glitchChar();
                this.target += this.text[this.target.length];
                this.displayText = tempText;
                setTimeout(() => this.updateDisplay(), this.currentSpeed);
            } else {
                this.displayText = this.text;
            }
        },
        glitchChar() {
            const r = Math.ceil(Math.random() * 10) % this.text.length;
            return this.randomChars[r];
        }
    },
    created() {
        this.currentSpeed = this.speed || this.defaultSpeed;
    },
    mounted() {
        this.updateDisplay();
    },
}
</script>