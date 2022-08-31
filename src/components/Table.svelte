<script lang="ts">
	import DataTable, { Head, Body, Row, Cell } from '@smui/data-table';
	import Checkbox from '@smui/checkbox';
	import Button, { Group, GroupItem, Label, Icon } from '@smui/button';
	import type { MenuComponentDev } from '@smui/menu';
	import Menu from '@smui/menu';
	import List, { Item, Separator, Text } from '@smui/list';

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
		</Body>
	</DataTable>
</main>
