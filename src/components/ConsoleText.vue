<template>
      <div class='console-container'>
          <span>
              {{text}}
          </span>
          
          <span :class=" showUnderscore ? 'console-underscore' : 'console-underscore hidden' " id='console'>
              &#95;
          </span>
        </div>
</template>

<script>
export default {
    props: {
        fromHome: {
            type: Boolean,
            default: false
        },
        staticText: {
            type:String,
            default: 'Hello'
        },
        dynamicText: {
            type:String,
            default: 'World'
        },
        delay: {
            type:Number,
            default: 500
        },
        speed: {
            type:Number,
            default: 100
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
        addString(text , speed = this.speed, delay = this.delay) {
            let desiredText = text.split('')
            desiredText.forEach((element , i) => {
                setTimeout( () => {
                    this.text = this.text.concat(element)
                },speed * i + delay)
            });
        },
        removeletters(num , speed = this.speed) {
            for (let i = 0; i < num; i++) {
                setTimeout( () => {
                    this.text = this.text.slice(0,-1)
                },speed * i + this.delay)
                
            }
        }
    },
    data() {
        return {
            showUnderscore: false,
            text:">",
            oldDynamicText:"",
            animate:false,
        }

    },
    watch: {
        dynamicText: function(newVal) {
            if (this.animate) {
                this.removeletters(this.oldDynamicText.length , this.speed * 2)
                this.addString(newVal ,this.speed * 2 , this.oldDynamicText.length * this.speed * 2  + (2 * this.delay) )
            }
            else {
                this.addString(this.staticText + this.dynamicText)
            }

            this.animate = true
            this.oldDynamicText = newVal

        }
    },
    mounted() {
        setInterval(this.blink, 400)
        if (this.fromHome) {
            this.addString(this.staticText + this.dynamicText)
            this.text = this.startingString
            this.animate = true

        }
        else {
            console.log(this.dynamicText)
        }
    }
}
</script>

<style scoped>


.hidden {
    opacity: 0;
}

.console-container {
  font-family:monospace;
  text-align:center;
  color:black;
}


.console-underscore {
  position:relative;
  top:-0.14em;
}

span{
display: inline-block;
}


</style>