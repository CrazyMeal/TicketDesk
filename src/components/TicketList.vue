<<template>
    <v-layout row wrap>
	    <ticket-item 
			v-for="ticket in tickets"
			v-bind:ticket="ticket"
			v-bind:key="ticket.reference" 
			v-on:removeticketitem="removeTicket"
            >
		</ticket-item>
	</v-layout>
</template>

<<script>
import TicketItem from './TicketItem'

export default {
    name: 'ticket-list',
    props: ['tickets'],
    data () {
        return {
        }
    },
    methods: {
        removeTicket: function (ticket) {
            console.log('Trying to remove item ' + ticket)
            var index = this.tickets.indexOf(ticket)
            console.log('Index is: ' + index)
            this.tickets.splice(index, 1)
        }
    },
    components: {
        'ticket-item': TicketItem
    }
}
</script>
