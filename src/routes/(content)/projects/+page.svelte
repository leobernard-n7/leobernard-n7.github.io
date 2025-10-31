<script lang="ts">
	import CardGrid from "../../CardGrid.svelte";

	let projects = [
		{
			label: 'Lisa & Olive',
            img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
			value: '1'
		},
		{
			label: 'Miniature Kaiju',
            img: '/src/lib/assets/images/art/miniature_kaiju.png',
			value: '2'
		},
		{
			label: 'Sunnyside Cruise',
            img: '/src/lib/assets/images/art/sunnyside_cruise.png',
			value: '3'
		},
		{
			label: 'Doodle Art',
            img: '/src/lib/assets/images/art/doodle_art_vertical.png',
			value: '4'
		},
		// {
		// 	label: 'Test 5',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '5'
		// },
		// {
		// 	label: 'Test 6',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '6'
		// },
		// {
		// 	label: 'Test 7',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '7'
		// },
		// {
		// 	label: 'Test 8',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '8'
		// },
		// {
		// 	label: 'Test 9',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '9'
		// },
		// {
		// 	label: 'Test 10',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '10'
		// },
		// {
		// 	label: 'Test 11',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '11'
		// },
		// {
		// 	label: 'Test 12',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '12'
		// },
		// {
		// 	label: 'Test 13',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '13'
		// },
		// {
		// 	label: 'Test 14',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '14'
		// },
		// {
		// 	label: 'Test 15',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '15'
		// },
		// {
		// 	label: 'Test 16',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '16'
		// },
		// {
		// 	label: 'Test 17',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '17'
		// },
		// {
		// 	label: 'Test 18',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '18'
		// },
		// {
		// 	label: 'Test 19',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '19'
		// },
		// {
		// 	label: 'Test 20',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '20'
		// },
		// {
		// 	label: 'Test 21',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '21'
		// },
		// {
		// 	label: 'Test 22',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '22'
		// },
		// {
		// 	label: 'Test 23',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '23'
		// },
		// {
		// 	label: 'Test 24',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '24'
		// },
		// {
		// 	label: 'Test 25',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '25'
		// },
		// {
		// 	label: 'Test 26',
        //     img: '/src/lib/assets/images/art/lisa_and_olive_square.png',
		// 	value: '26'
		// }
	];
</script>

<CardGrid cards={projects} />

<style>
</style>
