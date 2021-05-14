<template>
  <div>
      <div class='word-container'>
          <span>
              {{text}}
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
            default: 400
        },
        speed: {
            type:Number,
            default: 50
        },
        startingString: {
            type: String,
            default: ""
        }
    },
    methods: {
        addLetter(desiredText) {
            var characters       = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
            var charactersLength = characters.length;
            desiredText.forEach((element , i) => {
                setTimeout( () => {
                    this.text = this.text.concat(characters.charAt(Math.floor(Math.random() * charactersLength)))
                    this.text = this.text.concat(characters.charAt(Math.floor(Math.random() * charactersLength)))
                },this.speed * i + (this.delay - this.speed));
                setTimeout( () => {
                    this.text = this.text.slice(0,-2)
                    this.text = this.text.concat(element)
                },this.speed * i + this.delay);
            });
        }
    },
    data() {
        return {
            text:"",
        }

    },
    mounted() {
        this.addLetter(this.finalText.split(''))
        this.text = this.startingString
    }
}
</script>

<style scoped>




.word-container {
 
  font-family:monospace;
  font-size: 5vh;
  text-align:center;
  display: block;
  position:relative;
  color:black;
  top:0;
  bottom:0;
  left:0;
  right:0;
  margin:auto;
  transition: 0.5s;


  
}

.word-container:hover {
    color: rgb(255, 72, 0);
    font-weight: 400;
}

</style>