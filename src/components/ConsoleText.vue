<template>
      <div class='console-container'>
          <span>
              {{startingString}}
          </span>
          <span>
              {{preText}}
          </span>
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
        checkAndWrite() {
            if (this.hasChanged) {
                
                if (this.toDelete > 0) {
                    this.dynamicPart.pop()
                    this.toDelete = this.toDelete - 1
                }
                else if (this.inLine.length != 0 ) {
                    this.dynamicPart = this.dynamicPart.concat(this.inLine.shift())
                    console.log(this.dynamicPart)

                }
                else if (this.inLine.length == 0) {
                    this.hasChanged = false
                }
            }
        },
        firstWrite() {
            let desiredText = this.staticText.split('')
            desiredText.forEach((element , i) => {
                setTimeout( () => {
                    this.preText = this.preText.concat(element)
                },this.speed * i + this.delay)
            });
        }
    },
    data() {
        return {
            showUnderscore: false,
            dynamicPart: [],
            inLine: [],
            toDelete: 0,
            hasChanged: false,
            preText: ""
        }

    },
    computed: {
        text: function() {
            return  this.dynamicPart.join('')
        }
    },
    watch: {
        dynamicText: function(newVal) {
            this.inLine = newVal.split('')
            this.hasChanged = true
            this.toDelete = this.dynamicPart.length + 1
        }
    },
    mounted() {
        setInterval(this.blink, 400)
        this.firstWrite()
        setTimeout(() => {
            setInterval(this.checkAndWrite, this.speed);
        }, this.speed * this.staticText.length + this.delay);
        

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