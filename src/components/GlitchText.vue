<template>
    <p>{{ displayText }}</p>
    <button @click="displayText += displayText">Click</button>
</template>

<script>
export default {
    props: {
        text: String
    },
    data() {
        return {
            displayText: "",
            randomChars: "~!@#$%^&*()<>/",
            idxText: 0
        }
    },
    methods: {
        updateDisplay () {
            let tempText = this.displayText.split("");
            if(this.displayText.length < this.text.length + 1) {
                const rndChr = this.glitchChar();
                tempText.push(rndChr);
                for(let i = 0; i < this.idxText; i++) {
                    tempText[i] = this.text[i];
                }
                this.idxText++;
                this.displayText = tempText.join("");
                setTimeout(this.updateDisplay, 100);
            } else {
                tempText.pop();
                this.displayText = tempText.join("");
            }
        },
        glitchChar() {
            const r = Math.ceil(Math.random() * 10) % this.text.length;
            return this.randomChars[r];
        }
    },
    mounted() {
        this.updateDisplay();
    },
    watch: {
        displayText: {
            handler(val) {
                console.log("under watch, val is: ", val)
            }
        }
    }
}
</script>