<script>
	import { ApolloClient, InMemoryCache, gql } from '@apollo/client/core';
	import { setClient } from 'svelte-apollo';
  import { query } from 'svelte-apollo';

	setClient(new ApolloClient({
		uri: 'http://localhost:5001/graphql',
		cache: new InMemoryCache(),
	}));
  

	const GET_CLIENTS = gql`
 query {
    clients {
      id
      name
      email
      phone
    }
  }
`;
</script>

<div>Clients</div>
<p></p>
