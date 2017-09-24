<<template>
    <v-flex xs6 offset-xs3>
		<v-card class="elevation-2" hover>
			<v-card-title primary-title>
				<div style="width:100%">
			    	<h3 class="headline mb-0">{{ ticket.reference }}</h3>
			    	<v-layout row fluid>
				    	<v-flex xs6>
					    	Emitter: {{ ticket.emitter }} <br />
							Affected to: {{ ticket.affectedTo }} <br />
							Description: {{ ticket.description }}
						</v-flex>
						<v-flex xs6>
							Creation date: {{ ticket.creationDate }} <br />
							Notification: {{ ticket.notificationDate }} <br />
							Taken into account: {{ ticket.takenIntoAccountDate }} <br />
						</v-flex>
					</v-layout>
			    </div>
			    <v-btn dark small absolute bottom right fab primary
					v-on:click="removeTicket(ticket)">
	           		<v-icon>remove</v-icon>
	           	</v-btn>
			</v-card-title>
		</v-card>
	</v-flex>
</template>

<<script>
export default {
    name: 'ticket-item',
    props: ['ticket'],
    data () {
        return {
        }
    },
    methods: {
        removeTicket: function (ticket) {
            console.log('Emitting remove item event')
            this.$emit('removeticketitem', ticket)
        }
    }
}
</script>

