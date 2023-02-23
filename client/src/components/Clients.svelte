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
  <table class="table table-hover mt-3">
    <thead>
      <tr>
        <th>Name</th>
        <th>Email</th>
        <th>Phone</th>
        <th></th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>{client.name}</td>
        <td>{client.email}</td>
        <td>{client.phone}</td>
      </tr>
    </tbody>
  </table>
  <br/>
  {/each}
{/if}
</div>