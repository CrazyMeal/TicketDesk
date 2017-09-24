<template>
  <div id="app">
    <v-app id="example-1" toolbar footer>
      <v-navigation-drawer persistent v-model="drawer" light enable-resize-watcher overflow>
        <v-list dense>
          <v-list-tile>
            <v-list-tile-action>
              <v-icon>home</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>Home</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
      </v-navigation-drawer>
      <v-toolbar class="light-blue darken-1" dark>
        <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
        <v-toolbar-title>Active tickets list</v-toolbar-title>
      </v-toolbar>
      <main>
        <v-container fluid grid-list-xl class="elevation-0">
          <ticket-input v-on:createnewticket="createNewTicket"></ticket-input>
          <v-slide-y-transition>
            <v-layout row wrap v-if="alertShow">
              <v-alert error value="true">Ticket's reference has to be numeric</v-alert>
            </v-layout>
          </v-slide-y-transition>
          <ticket-list v-bind:tickets="tickets">
          </ticket-list>
        </v-container>
      </main>
      <v-footer class="light-blue darken-1">
        <span class="white--text">Made with love</span>
      </v-footer>
    </v-app>
  </div>
</template>

<script>
import TicketList from './components/TicketList'
import TicketInput from './components/TicketInput'

export default {
  name: 'app',
  data () {
    return {
      drawer: true,
      alertShow: false,
      tickets: [
        {
          reference: '12345',
          emitter: 'Robert Dupont',
          affectedTo: 'Mireille Dubois',
          description: 'Cannot do anything!',
          creationDate: '02 sept 2017 09:58',
          notificationDate: '02 sept 2017 10:00',
          takenIntoAccountDate: '02 sept 2017 10:03'
        }
      ]
    }
  },
  methods: {
    createNewTicket: function (ticket) {
      console.log('Received ticket')
      this.tickets.push(ticket)
    }
  },
  components: {
    'ticket-list': TicketList,
    'ticket-input': TicketInput
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
