<template>
      <div :class="{'word-container': true , 'hoverable': hoverable}">
              {{text}}
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
        },
        hoverable: {
            type: Boolean,
            default: false
        },
        scrambleChars: {
            tyoe: Number,
            default: 1
        }
    },
    methods: {
        addLetter(desiredText) {
            var characters       = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789@#$%^&';
            var charactersLength = characters.length;
            desiredText.forEach((element , i) => {
                setTimeout( () => {
                    this.text = this.text.concat(characters.charAt(Math.floor(Math.random() * charactersLength)))
                },this.speed * (i) + this.delay );
                setTimeout( () => {
                    this.text = this.text.substr(0,i) + element + this.text.substr(i+1)
                },this.speed * (i + this.scrambleChars) + this.delay);
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
 
  position:relative;
  color:black;
  transition: 0.5s;

  
}

.hoverable:hover {
    color: rgb(255, 72, 0);
    font-weight: 450;
    cursor: pointer;
}

</style>