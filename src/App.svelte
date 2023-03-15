<script>
	const formatter = new Intl.NumberFormat('no-NB', {
  style: 'currency',
  currency: 'NOK',
	});
	let tax = 0.4;
	let grossInput = 0; 
	$: taxToPay = grossInput * tax;
	$: net = grossInput - (grossInput * tax);
	$: aga = grossInput * 0.141;
	$: vac = grossInput * 0.102;
	$: total = +grossInput + aga + vac;
</script>

<main>
	<h1>Ratolakluk</h1>
	<label for="brutto-input">Brutto</label>
	<input name="brutto-input" type="text" placeholder="brutto" bind:value={grossInput}/>
	<input name="brutto-input" type="range" step="1000" min="5000" max="2500000"placeholder="brutto" bind:value={grossInput}/>
	<label for="tax-input">Skatteprosent</label>
	<input name="tax-input" type="text" placeholder="skatteprosent"bind:value={tax}>
	<span>Skatt: {formatter.format(taxToPay)}</span>
	<span>AGA: {formatter.format(aga)}</span>
	<span>Ferie: {formatter.format(vac)}</span>
	<br />
	<br />
	<strong><span>Brutto: {formatter.format(grossInput)}</span></strong>
	<strong><span>Netto: {formatter.format(net)}</span></strong>
	<span>Total for AS: {formatter.format(total)}</span>
</main>

<style>
	main {
		display:flex;
		flex-direction: column;
	}
</style>