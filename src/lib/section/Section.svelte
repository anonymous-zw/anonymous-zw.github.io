<script>
	export let style;
	export let image;
	export let title;
	export let text;
	export let page;
</script>

<div class="section style-{style}">
	<div class="wrapper">
		<img class="section-image" src={image} alt={title}>
	</div>
	<div class="info">
		<h1>{title}</h1>
		<p>{text}</p>
		<a href={page}>See more...</a>
	</div>
</div>

<style>
	h1 {
		font-family: "Playfair Display";
		color: #3f3d34;
	}

	.section, .style-0 {
		height: 60vh;
		margin: 0 2em;
		margin-bottom: 2em;
		display: grid;
		grid-template-columns: 50% auto;
		grid-template-rows: 100%;
		gap: 2em;
	}

	.style-1 {
		grid-template-columns: auto 50%;
	}
	
	.style-1 img {
		order: 1;
	}

	.style-1 .info {
		order: -1;
	}

	img, .wrapper {
		height: 100%;
		width: 100%;
		border-radius: 2em;
	}
	
	img {
		object-fit: cover;
		object-position: center;
		filter: grayscale(0.6);
	}

	.wrapper {
		overflow: hidden;
	}
</style>