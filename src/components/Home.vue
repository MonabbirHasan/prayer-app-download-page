<template>
    <div class="wrapper">
        <h1>welcome download now</h1>
        <a v-on:click="Like()" href="https://mega.nz/file/waN3RKhA#KiSNe1r0B9QoQdaduX_g4rhjZE92bRtz6t-MufqSSfQ" download="https://mega.nz/file/waN3RKhA#KiSNe1r0B9QoQdaduX_g4rhjZE92bRtz6t-MufqSSfQ">DOWNLOAD</a>
        <div id="animat">
            <div id="app">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Home-page",
    data() {
        return {
            name: "welome"
        }
    },
    methods: {
        Like() {

            var download = 0
            var data = [
                { lilke: download = download + 1 }
            ]

            localStorage.setItem(Math.random(), JSON.stringify(data))
            console.log(JSON.parse(localStorage.getItem("download")))
        }
    }
}

const root = document.querySelector("#app");
let { innerHeight, innerWidth } = window;
console.log(innerHeight, innerWidth);
if (innerHeight < 300) {
    innerHeight = 50;
}
if (innerWidth < 300) {
    innerWidth = 50;
}

class Bubble {
    constructor() {
        this.bubbleSpan = undefined;
        this.handleNewBubble();
        this.color = this.randomColor();

        this.posY = this.randomNumber(innerHeight - 20, 20);
        this.posX = this.randomNumber(innerWidth - 20, 20);

        this.bubbleSpan.style.top = this.posY + "px";
        this.bubbleSpan.style.left = this.posX + "px";

        // setting height and width of the bubble
        this.height = this.randomNumber(6, 6);
        this.width = this.height;

        this.bubbleEnd.call(this.bubbleSpan, this.randomNumber(60, 30));
    }

    // creates and appends a new bubble in the DOM
    handleNewBubble() {
        this.bubbleSpan = document.createElement("span");
        this.bubbleSpan.classList.add("bubble");
        root.append(this.bubbleSpan);
        this.handlePosition();
        this.bubbleSpan.addEventListener("click", this.bubbleEnd);
    }

    handlePosition() {
        this.bubbleSpan.style.backgroundColor = this.color;
        this.bubbleSpan.style.height = this.height + "px";
        this.bubbleSpan.style.width = this.height + "px";

        this.posY = this.randomNumber(innerHeight - 20, 20);
        this.posX = this.randomNumber(innerWidth - 20, 20);

        this.bubbleSpan.style.top = this.posY + "px";
        this.bubbleSpan.style.left = this.posX + "px";

        const randomSec = this.randomNumber(40, 20);
        setTimeout(this.handlePosition.bind(this), randomSec); // calling for re-position of bubble
    }

    randomNumber(max, min) {
        return Math.floor(Math.random() * (max - min + 1) + min);
    }

    randomColor() {
        return `rgba(
        ${this.randomNumber(0, 255)},
        ${this.randomNumber(0, 255)},
        ${this.randomNumber(0, 255)}, 
        ${this.randomNumber(0.1, 1)})`;
    }

    bubbleEnd(removingTime = 0) {
        setTimeout(
            () => {
                requestAnimationFrame(() => this.classList.add("bubble--bust"));
            },
            removingTime === 0 ? removingTime : removingTime - 100
        );

        setTimeout(() => {
            requestAnimationFrame(() => this.remove());
            requestAnimationFrame(() => new Bubble());
        }, removingTime);
    }
}

// creating many bubble instance

setInterval(function () {
    requestAnimationFrame(() => new Bubble());
}, 300);

</script>

<style>
*,
*:before,
*:after {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    background: #ffebeb;
    background: rgba(240, 248, 255, 0.9);
    overflow: hidden;
}

.bubble {
    position: absolute;
    top: 0;
    left: 0;
    border-radius: 50%;
    cursor: pointer;
    transition: linear 2s, transform 0.2s;
}

.bubble:hover {
    transform: scale(1.7);
}

.bubble--bust {
    transform: scale(1.8);
}

body {
    margin: 0;
    padding: 0;
    overflow: hidden;
    font-family: 'Roboto', sans-serif;
    font-family: 'Roboto Mono', monospace;
}

#animat {
    width: 100%;
    height: 100vh;
}

.wrapper {
    padding: 10px;
    width: 100%;
    background-image: url("../assets/software.jpeg");
    background-repeat: no-repeat;
    background-size: cover;
    background-attachment: fixed;
    background-position: center;
    min-height: 100vh;
    justify-content: center;
    align-items: center;
    text-align: center;
    overflow: hidden;
    filter: brightness(1.20);

}

.wrapper a {
    padding: 10px 30px;
    background: #fc9400;
    border: 2px solid #eee;
    border-radius: 10px;
    color: #ffff;
    font-weight: bold;
    font-size: 17px;
    text-transform: uppercase;
    letter-spacing: 2px;
    clear: both;
    filter: drop-shadow(5px 5px 5px #236bf1);
    text-decoration: none;
    position: relative;
    top: 50vh;
    cursor: pointer;
    z-index: 100;
    margin: auto;
    vertical-align: middle;
}

.wrapper a:hover {
    filter: drop-shadow(0 0 0);
    background: black;
}

.wrapper h1 {
    font-weight: 900;
    color: white;
    font-size: 3rem;
    position: relative;
    top: 10vh;
    text-transform: uppercase;
    text-align: center;
    letter-spacing: 2px;
    animation: text 2s linear infinite;
    -webkit-text-stroke: #fc9400;
    -webkit-text-stroke-width: 1px;
   
}

@keyframes text {
    0% {
        filter: hue-rotate(0deg);
    }

    100% {
        filter: hue-rotate(360deg);
        transform-origin: bottom;
    }
}
</style>