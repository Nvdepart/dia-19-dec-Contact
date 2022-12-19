<template>
    <div>
        <h1>Contact Info</h1>
        <v-row>
            <v-col cols="12" sm="6">
                <v-text-field
                    v-model="nom"
                    :rules="[rules.required, rules.counter]"
                    label="Nom Participant"
                    counter
                    maxlength="20"
                ></v-text-field>
                <v-text-field
                    v-model="email"
                    :rules="[rules.required, rules.email]"
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
                </v-col>
            <v-col cols="12" sm="6">
                <h1>Resultat</h1>
            </v-col>
        </v-row>
    </div>
</template>


<script>
    export default {
        props:{
            nom:{
                type: String,
                default:""
            },
            email:{
                type: String,
                default:""
            },
        },
        data () {
            return {
                nom: 'Preliminary report',
                email: '',
                rules: {
                    required: value => !!value || 'Required.',
                    counter: value => value.length <= 20 || 'Max 20 characters',
                    email: value => {
                        const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
                        return pattern.test(value) || 'Invalid e-mail.'
                    },
                },
            }
        },
        methods:{
            afegirParticipant(){
                // push afegir el participant a l'array de participants

                this.participants.push(
                    {
                        nom:this.nom,
                        email:this.email
                    }
                )
            }
        }

    }

</script>