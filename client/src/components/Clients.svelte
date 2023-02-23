<script>
	import { gql } from '@apollo/client/core';
	import { query } from 'svelte-apollo';
	// import {client} from "../routes/+page.svelte"

	const GET_CLIENTS = gql`
		query getClients {
			clients {
				id
				name
				email
				phone
			}
		}
	`;
	const clients = query(GET_CLIENTS);
</script>

<div>Clients</div>
<div>
{#if $clients.loading}
  <p>Loading...</p>
{:else if $clients.error}
  <p>Error: Something Went Wrong</p>
{:else}
  {#each $clients.data.clients as client}
  <div> {client.email}</div>  
  <div>{client.id}</div>
  <div>{client.email}</div>
  <div>{client.phone}</div>
  <br/>
  {/each}
{/if}
</div>