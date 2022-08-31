<script lang="ts">
	import DataTable, { Head, Body, Row, Cell } from '@smui/data-table';
	import Checkbox from '@smui/checkbox';
	import Button, { Group, GroupItem, Label, Icon } from '@smui/button';
	import type { MenuComponentDev } from '@smui/menu';
	import Menu from '@smui/menu';
	import List, { Item, Separator, Text } from '@smui/list';

	$: selectedPrice = selected.reduce((total, option) => option.total + total, 0);

	let options = [
		{
			code: '123123123312',
			date: '22/02/1994',
			client: 'Gean Ferreira',
			paymentType: 'Cartão de crédito',
			status: 'Aguardando pagamento',
			total: 20000
		},
		{
			code: '123123123312',
			date: '22/02/1994',
			client: 'Arthur Fusco',
			paymentType: 'Cartão de crédito',
			status: 'Aguardando pagamento',
			total: 20000
		},
		{
			code: '123123123312',
			date: '22/02/1994',
			client: 'Pedro Henrique',
			paymentType: 'Cartão de crédito',
			status: 'Aguardando pagamento',
			total: 20000
		},
		{
			code: '123123123312',
			date: '22/02/1994',
			client: 'João',
			paymentType: 'Cartão de crédito',
			status: 'Aguardando pagamento',
			total: 20000
		},
		{
			code: '123123123312',
			date: '22/02/1994',
			client: 'Alasca',
			paymentType: 'Cartão de crédito',
			status: 'Aguardando pagamento',
			total: 20000
		}
	];

	let selected = [options[2]];
	let clicked = 0;
	let menu: MenuComponentDev;
	let menu2: MenuComponentDev;
</script>

<main style=" text-align: end; padding: 0 24px;">
	<Group variant="raised" style="margin: 0 24px 24px 0;">
		<Button on:click={() => clicked++} variant="raised">
			<Label>Ações</Label>
		</Button>
		<div use:GroupItem>
			<Button
				on:click={() => menu.setOpen(true)}
				variant="raised"
				style="padding: 0; min-width: 36px;"
			>
				<Icon class="material-icons" style="margin: 0;">arrow_drop_down</Icon>
			</Button>
			<Menu bind:this={menu} anchorCorner="TOP_LEFT">
				<List>
					<Item on:SMUI:action={() => clicked++}>
						<Text>Deletar</Text>
					</Item>
				</List>
			</Menu>
		</div>
	</Group>

	<DataTable style="width: 100%;">
		<Head>
			<Row>
				<Cell checkbox>
					<Checkbox />
				</Cell>
				<Cell>CÓDIGO</Cell>
				<Cell>DATA</Cell>
				<Cell>CLIENTE</Cell>
				<Cell>PAGAMENTO</Cell>
				<Cell>SITUAÇÃO</Cell>
				<Cell>VALOR TOTAL</Cell>
				<Cell></Cell>
			</Row>
		</Head>
		<Body>
			{#each options as option (option.client)}
				<Row>
					<Cell checkbox>
						<Checkbox bind:group={selected} value={option} valueKey={option.client} />
					</Cell>
					<Cell>{option.code}</Cell>
					<Cell>{option.date}</Cell>
					<Cell>{option.client}</Cell>
					<Cell>{option.paymentType}</Cell>
					<Cell>{option.status}</Cell>
					<Cell>{option.total}</Cell>
					<Cell
						><Button color="secondary" on:click={() => console.log('funcionei')} variant="outlined">
							<Label>MAIS DETALHES</Label>
						</Button></Cell
					>
				</Row>
			{/each}
		</Body>
	</DataTable>
	<pre class="status">Selected: {selected.map((option) => option.client).join(', ')}</pre>
	<pre class="status">Total: {selectedPrice}</pre>
</main>
