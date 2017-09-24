<template>
    <v-layout text-xs-center row wrap>
        <v-flex xs12>
            <v-layout row wrap>
                <v-flex xs4>
                    <v-text-field name="input-reference" label="Reference" id="ticket-reference" v-model="ticketInput"></v-text-field>
                    <v-text-field name="input-emitter" label="Emitter" id="ticket-emitter" v-model="ticketInput"></v-text-field>
                    <v-text-field name="input-affected" label="Affected to" id="ticket-affected" v-model="ticketInput"></v-text-field>
                </v-flex>
                <v-flex xs4>
                    <v-text-field name="input-date-creation" label="Creation date" id="ticket-date-creation" v-model="ticketInput"></v-text-field>
                    <v-text-field name="input-date-notification" label="Notification date" id="ticket-date-notification" v-model="ticketInput"></v-text-field>
                    <v-text-field name="input-date-taken" label="Taken into account" id="ticket-taken" v-model="ticketInput"></v-text-field>
                </v-flex>
                <v-flex xs4>
                    <v-select v-bind:items="dropdown_icon" label="Application" autocomplete></v-select>
                    <v-text-field name="input-description" label="Description" id="ticket-description" v-model="ticketInput"></v-text-field>
                </v-flex>
            </v-layout>
            <v-btn light v-on:click="addNewTicket">Add new ticket</v-btn>
        </v-flex>
    </v-layout>
</template>
<script>
export default {
    name: 'ticket-input',
    data () {
        return {
            ticketInput: '',
            dropdown_icon: ['list', 'favorite', 'delete']
        }
    },
    methods: {
        addNewTicket: function () {
            console.log('Trying to add new Ticket')
            if (isNaN(this.ticketInput)) {
                console.log('Input value is not numeric, showing alert')
                this.alertShow = true
            } else {
                var moment = require('moment')
                console.log('Input value is numeric, adding new ticket with reference ' + this.ticketInput)
                var creationDate = moment().format('DD MMM YYYY HH:mm')
                var notificationDate = moment().add(10, 'm').format('DD MMM YYYY HH:mm')
                var takenIntoAccountDate = moment().add(13, 'm').format('DD MMM YYYY HH:mm')
                var ticket = {
                    reference: this.ticketInput,
                    creationDate: creationDate,
                    emitter: 'Michel Dupont',
                    notificationDate: notificationDate,
                    takenIntoAccountDate: takenIntoAccountDate,
                    affectedTo: 'ABC',
                    description: 'Error detected in production'
                }
                this.$emit('createnewticket', ticket)
                this.ticketInput = ''
                this.alertShow = false
            }
        }
    }
}
</script>

