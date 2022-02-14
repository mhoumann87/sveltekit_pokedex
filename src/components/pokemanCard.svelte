<script>
	export let info;
</script>

<a
	class="list-none p-6 bg-gray-100 text-gray-800 text-center rounded-md shadow-sm hover:shadow-md flex flex-col items-center"
	href={`/pokemon/${info.id}`}
>
	<img class="h-40 w-40" src={info.image} alt={info.name} />
	<h2 class="text-2xl uppercase">{info.id}. {info.name}</h2>
</a>
