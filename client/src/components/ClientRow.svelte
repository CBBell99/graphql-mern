<script>
	export let client;
	import Fa from 'svelte-fa';
	import { faTrash } from '@fortawesome/free-solid-svg-icons';
	import { DELETE_CLIENT } from '../mutations/clientMutations';
	import { mutation } from 'svelte-apollo';
	import { GET_CLIENTS } from '../queries/clientQueries';

	const deleteClient = mutation(DELETE_CLIENT, {
		variables: { id: client.id },
		// refetchQueries: [{ query: GET_CLIENTS }],
    update(cache, {data: {deleteClient}}) {
      const {clients} = cache.readQuery({
        query: GET_CLIENTS
      })
        cache.writeQuery({
          query: GET_CLIENTS,
          data: {clients: clients.filter(client => client.id !== deleteClient.id)}
      })
    }
	});
</script>

<tbody>
	<tr>
		<td>{client.name}</td>
		<td>{client.email}</td>
		<td>{client.phone}</td>
		<td>
			<button class="btn btn-danger btn-sm" on:click={deleteClient}>
				<Fa icon={faTrash} />
			</button>
		</td>
	</tr>
</tbody>
