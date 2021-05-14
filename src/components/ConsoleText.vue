<template>
  <div>
      <div class='console-container'>
          <span>
              {{text}}
          </span>
          <span :class=" showUnderscore ? 'console-underscore' : 'console-underscore hidden' " id='console'>
              &#95;
          </span>
        </div>
  </div>
</template>

<script>
export default {
    props: {
        finalText: {
            type:String
        },
        delay: {
            type:Number,
            default: 500
        },
        speed: {
            type:Number,
            default: 200
        },
        startingString: {
            type: String,
            default: ">"
        }
    },
    methods: {
        blink() {
            this.showUnderscore = !this.showUnderscore
        },
        addLetter(desiredText) {
            
            desiredText.forEach((element , i) => {
                setTimeout( () => {
                    this.text = this.text.concat(element)
                },this.speed * i + this.delay)
            });
        }
    },
    data() {
        return {
            showUnderscore: false,
            text:">",
        }

    },
    created() {
        setInterval(this.blink, 400)
        this.addLetter(this.finalText.split(''))
        this.text = this.startingString
    }
}
</script>

<style>


.hidden {
    opacity: 0;
}

.console-container {
 
  font-family:monospace;
  font-size: 5vh;
  text-align:center;
  height:20vh;
  width:100vw;
  display: block;
  color:black;
  top:0;
  bottom:0;
  left:0;
  right:0;
  margin:auto;
}


.console-underscore {
  position:relative;
  top:-0.14em;
  left:-1rem;
}
</style>