<script>
	import { ApolloClient, InMemoryCache } from '@apollo/client/core';
	import { setClient } from '$svelte-apollo/client';

	const client = new ApolloClient({
		uri: 'http://localhost:5001/graphql',
		cache: new InMemoryCache(),
	});

	setClient(client);
</script>

<div class="container">
	<h1>Hello World</h1>
</div>
