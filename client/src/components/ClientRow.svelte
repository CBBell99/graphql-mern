<script>
  export let client
  import Fa from "svelte-fa"
  import {faTrash} from "@fortawesome/free-solid-svg-icons"
</script>

<tr>
	<td>{client.name}</td>
	<td>{client.email}</td>
	<td>{client.phone}</td>
  <td>
    <button class="btn btn-danger btn-sm">
      <Fa icon={faTrash}/>
     </button>
  </td>
</tr>
