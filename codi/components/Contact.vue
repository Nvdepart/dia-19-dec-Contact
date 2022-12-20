<template>
    <div>
        <h1>Contact Info</h1>
        <v-row>
            <v-col cols="12" sm="6">
                <v-text-field
                    v-model="nom"
                    
                    label="Nom Participant"
                    counter
                    maxlength="20"
                ></v-text-field>
                <v-text-field
                    v-model="email"
                   
                    label="E-mail"
                ></v-text-field>
                <v-btn @click="afegirParticipant()"
                    class="mx-2"
                    fab
                    color="green"
                    >
                    <v-icon>
                        mdi-plus
                    </v-icon>
                </v-btn>
                
                <v-data-table 
                class="table"
                dark
                :headers="participant"
                :items="participants"
                :items-per-page=10
                item-key="nom"></v-data-table>
                </v-col>
            <v-col cols="12" sm="6">
                <h1>Resultat</h1>
            </v-col>
        </v-row>
    </div>
</template>


<script>
    export default {
        /*props:{
            nom:{
                type: String,
                default:""
            },
            email:{
                type: String,
                default:""
            },
        },*/
        data () {
            return {
                participant:[{
                    text: 'Nom participant',
                    align:'start',
                    value:'nom'
                },
                {
                    text:'Email', value:'email'
                }
            ],
                participants:[
                        {
                        nom:"Dani",
                        email:"dani@gmail.com"
                        },
                        {
                        nom:"Paula",
                        email:"paula@gmail.com"
                        }
                    ],
                    /*rules: {
                        required: value => !!value || 'Required.',
                        counter: value => value.length <= 20 || 'Max 20 characters',
                        email: value => {
                            const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
                            return pattern.test(value) || 'Invalid e-mail.'
                        },
                    },*/


                nom:"",
                email:""
                
            }
        },
        methods:{
            afegirParticipant(){
                // push afegir el participant a l'array de participants
                if(!this.nom || !this.email){
                    return
                }
                this.participants.push(
                    {
                        nom:this.nom,
                        email:this.email
                    }
                )
                this.nom=""
                this.email=""
            }
        }

    }

</script>

<style>
.table{
    border: 1px solid;
    text-align: center;
    background-color: rgb(95, 38, 194);
    
}

</style>