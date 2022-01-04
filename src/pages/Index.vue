<template>
	<q-layout class="">
		<div>
      		<div class="absolute-center">

			<avatar style="width: 60vw; height:40vh;" :eye="this.model_eye" :mouth="this.model_mouth" :hair="this.model_hair" :shirt="this.model_shirt"/>
		</div>
		</div>
          <q-toolbar class="q-mt-xl fixed-top bg-primary text-white shadow-2 row items-start">

      <q-fab
      flat
      class="col" :icon="'img:'+option.icon"
       direction="down"
       v-for="option in options"
       v-bind:key="option.name"
       >
			   <q-color v-if="option.name === 'shirt'" v-model="this.color"
         no-header no-footer class="my-picker" @Change="this.model_shirt = this.color"/>
         <q-fab-action
            color="primary"
            v-for="items in option.options_body" v-bind:key="items.name"
            :icon="'img:'+items.src"
            @Click="onItemClick(option.name, items.src, items.name)"
         />

      </q-fab>

    </q-toolbar>
	</q-layout>
</template>
<script>
import { ref, onMounted } from 'vue'
import { useStore } from 'vuex'
import avatar from 'components/Avatar_Component.vue'

export default {
	components:{
		avatar
	},
  data() {
     const $store = useStore()
     const icon_shirt =  "https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fcamisa%2Fshirt-Jersey.png?alt=media&token=9fee9e47-c080-4d3e-947e-ba31b0bb8327"
     const icon_hair = "https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fpelo%2Fpelo-short1.svg?alt=media&token=eaedf07d-e00c-4e42-9393-5696c6a6e78c"
     const icon_eye = "https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fojos%2Feye-regular.svg?alt=media&token=eef5add8-8a25-4449-87ce-9ffc96608a95"
     const icon_mouth ="https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fboca%2Fcrazy.svg?alt=media&token=2d4351be-8599-4b90-b49a-470c32723233"
		 var model_eye = ref(null)
		 var model_hair = {
       src: ref(null), 
       height: ref(null),
       width: 0
     }
		 var model_mouth = " "
		 var model_shirt = " "
		 var color = " "
      onMounted(() => {

      })
		 return {
      model_eye,
			model_hair,
			model_mouth,
      model_shirt,
			avatar,
      registro: false,
      disable: ref(false),
			color,
      options: [
        {
            name:"eye",
            icon: icon_eye,
            options_body:[
               { src: 'https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/eye-angry.svg?alt=media&token=cf164313-c42b-47dd-bd55-2df81342503a' , name: 'angry'},
               { src: 'https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fojos%2Feye-cry.svg?alt=media&token=4ab98e7b-dcd9-43d4-af5b-36b9de2d2ae5' , name: 'sad'},
               { src: 'https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fojos%2Feye-regular.svg?alt=media&token=eef5add8-8a25-4449-87ce-9ffc96608a95' , name: 'happy'},
               { src: 'https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fojos%2Feye-sad.svg?alt=media&token=7b79d569-b1d8-4a8a-b625-41a168730cce' , name: 'sad'},
            ],
        },
        {
            name:"mouth",
            icon: icon_mouth,
            options_body:[
               { src: 'https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fboca%2Fmouth-regular.svg?alt=media&token=fb653f5c-0075-4f2d-8642-c00614b12db2' , name: 'scared'},
               { src: 'https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/Mouth_Angry.png?alt=media&token=5b3a7b58-8414-4766-ab1f-ce657e60ecd2' , name: 'angry'},
               { src: 'https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fboca%2Fcrazy.svg?alt=media&token=2d4351be-8599-4b90-b49a-470c32723233' , name: 'happy'},
               { src: 'https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fboca%2Fmouth-smile.svg?alt=media&token=a987a2b8-7f37-47e1-a74e-9de0ae730b04' , name: 'sad'},
               {
                 src:'https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fboca%2Fmouth-surprise.png?alt=media&token=0d056dab-59a2-4050-bac1-bc175053d555'
               },
               {
                 src: 'https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fboca%2Fmouth-sad.svg?alt=media&token=72cc6ba3-0814-4d3a-92f8-b4cbf1aa48f5'
               }
            ]
        },
        {
            name:"hair",
            icon: icon_hair,
            options_body:[
               { src: 'https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fpelo%2Fpelo-short2.svg?alt=media&token=398ca4e5-ffa7-47e1-a26d-520d98f83925' , name: '1'},
               { src: 'https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fpelo%2Fpelo3.svg?alt=media&token=a27b7921-151a-4ca6-8ffc-40ebe91479d3' , name: '2'},
               { src: 'https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fpelo%2Fpelo-short1.svg?alt=media&token=eaedf07d-e00c-4e42-9393-5696c6a6e78c' , name: '3'},
               { src: 'https://firebasestorage.googleapis.com/v0/b/sename-app.appspot.com/o/avatar%2Fpelo%2Fpelo4.svg?alt=media&token=02d8c3fa-309b-495a-97e7-21d80e069088' , name: '4'},
            ]
        },
        {
            name:"shirt",
            icon: icon_shirt,
            options_body:[

         ]
        }
      ],
      onItemClick (body, option, name) {
        if(body === "eye")
        {
          
					this.model_eye = option;
        }
				if(body === "mouth")
        {
					this.model_mouth = option;
        }
				if(body === "hair")
        {
					this.model_hair.src = option;
          if(name == '1'){
            this.model_hair.height = 80;
            this.model_hair.width = 80;
            this.model_hair.x = 45;
          }
          if(name == '3'){
            this.model_hair.height = 80;
            this.model_hair.width = 90;
            this.model_hair.x = 40;
          }
          if(name == '4'){
            this.model_hair.height = 150;
          }
          if(name == '2'){
            this.model_hair.height = 150;
            this.model_hair.width = 120;
            this.model_hair.x = 20;
          }
        }
				if(body === "shirt")
			  {
					this.model_shirt = color;
          console.log(color)
				}
      }
    }
  },
  methods:{
   async onSubmit(){
     if(!this.disable){
       this.disable = true
      if(this.route.includes('bar')){
        this.$store.commit('Modificar_Mensaje', this.$store.getters.info_emocion[3].Avatar[0].text[1])
        this.$store.commit('Modificar_Audio', this.$store.getters.info_emocion[3].Avatar[0].audio[1])
        console.log(this.$store.getters.audio +" audio ", this.$store.getters.mensaje + "mensaje")
      }
      var data = {
          hair: this.model_hair,
          eye: this.model_eye,
          shirt: this.model_shirt,
          mouth: this.model_mouth,
          user: Cookies.get('user').Nombre,
          date: output,
          emocion: 'registro'
        }
      if(this.route.includes('bar')){
                data.emocion = emocion

        this.$store.commit('Load_App_Avatar', data)
        
        if (this.emocion == "alegria") {
          setTimeout(() => {
                this.$store.commit('Route_Alegria')
          },13000)
            }
            if (this.emocion == "miedo") {
              setTimeout(() => {
                this.$store.commit('Route_Miedo')
              },16000)
            }

            if (this.emocion == "enojo") {
              setTimeout(() => {
                this.$store.commit('Route_Enojo')
              },18000)
            }

            if (this.emocion == "tristeza") {
              setTimeout(() => {
                this.$store.commit('Route_Tristeza')
              },17000)
            }
          
      }
      console.log(this.route)
      if(this.route.includes('auth')){
        console.log('enviado')
        this.$store.commit('Registrer_avatar', data)
      }
      
       } 

    }
  },
  mounted(){
   
  }
}
</script>
