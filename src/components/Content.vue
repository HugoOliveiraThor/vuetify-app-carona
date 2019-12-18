<template>
    <v-row align="center" justify="center">
          <v-col class="text-center">
            <v-row align="center">
              <v-btn 
                block 
                color="primary"
                @click="register"  
              >Registrar corrida</v-btn>
              <v-divider></v-divider>
            </v-row>
          </v-col>
        </v-row>
</template>

<script>
    export default {
        name:'Content',
        props: ['form'],
        mounted() {
            console.log('this.form;', this.form)
        },
        data() {
            return {}
        },
        methods: {
          register() {
            console.log('Registrou', this.form)
          }
        }
    }
</script>

<style lang="scss" scoped>

</style>