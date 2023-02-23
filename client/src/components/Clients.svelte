<script>
	import { query } from 'svelte-apollo';
	import ClientRow from './ClientRow.svelte';
	import Spinner from './Spinner.svelte';
	import { GET_CLIENTS } from '../queries/clientQueries';

	const clients = query(GET_CLIENTS);
</script>

<div>Clients</div>
<div>
	{#if $clients.loading}
		<Spinner />
	{:else if $clients.error}
		<p>Error: Something Went Wrong</p>
	{:else}
		<table class="table table-hover mt-3">
			<thead>
				<tr>
					<th>Name</th>
					<th>Email</th>
					<th>Phone</th>
					<th />
				</tr>
			</thead>
			{#each $clients.data.clients as client}
				<ClientRow {client} />
			{/each}
		</table>
	{/if}
</div>
