<script>
	import Clients from '../components/Clients.svelte';
	import { ApolloClient, InMemoryCache, gql } from '@apollo/client/core';
	import { setClient } from 'svelte-apollo';
  
	const client = new ApolloClient({
    uri: 'http://localhost:5001/graphql',
		cache: new InMemoryCache(),
	})
  
   setClient(client);


</script>

<div class="container">
	<Clients />
</div>
