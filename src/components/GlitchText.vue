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
                const r = Math.ceil(Math.random() * 10) % this.text.length;
                const rndChr = this.randomChars[r];
                tempText.push(rndChr);
                for(let i = 0; i < this.idxText; i++) {
                    tempText[i] = this.text[i];
                }
                this.idxText++;
                this.displayText = tempText.join("");
                setTimeout(this.updateDisplay, 300);
            } else {
                tempText.pop();
                this.displayText = tempText.join("");
            }
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