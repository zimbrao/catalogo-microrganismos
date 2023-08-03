<script>
    import { onMount } from "svelte";
    import CheckboxList from "./CheckboxList.svelte";
    import RoundedBox from "./RoundedBox.svelte";

    let apiURL =
      "https://dev.api.licenciamento.cos.ufrj.br:443/rest-gis/public_layer";
    let dataList = [];
    let grupo1, grupo2;

    async function fetchData() {
      const response = await fetch(apiURL);
      const data = await response.json();
      dataList = data.map(item => ({ name: item.name, checked: false }));
      grupo1 = dataList.filter(x => x.name > "P");
      grupo2 = dataList.filter(x => x.name <= "H");
    }

    onMount(fetchData);
</script>

<style>
  .checkbox-container {
    display: flex;
    gap: 20px;
    align-items: flex-start;
    padding: 10px;
  }
</style>
<RoundedBox label="Descrição"> 

<input type="text" bind:value={apiURL}><br>
<button on:click={fetchData}>Fetch Data</button>
</RoundedBox>


<RoundedBox label="Descrição"> 
	<div class="checkbox-container">
	  <CheckboxList label="Área" items={grupo1} />
	  <CheckboxList label="Restante" items={grupo2} />
	</div>
</RoundedBox>
