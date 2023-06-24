<script>
	import LoadingIndicator from './Loading.svelte';

	// /**
	//  * @type string
	//  */
	// export let cinemaType;
	/**
	 * @type Array<string>
	 */
	export let selectedKeywords;
	/**
	 * @type string
	 */
	export let specificDescriptors;
	/**
	 * @type Boolean
	 */
	export let loading;

	const groupedCategoryTypes = [
		// Emotion-related or values, quite significant in naming a baby.
		[
			'Love',
			'Joy',
			'Hope',
			'Grace',
			'Faith',
			'Courage',
			'Bravery',
			'Strength',
			'Honor',
			'Truth',
			'Compassion',
			'Charity',
			'Patience',
			'Wisdom',
			'Trust',
			'Peace',
			'Fidelity',
		],
		// These might signify the child's potential characteristics.
		[
			'Kindness',
			'Lively',
			'Active',
			'Vitality',
			'Passion',
			'Dynamic',
			'Playful',
			'Strong',
			'Masculine',
			'Enthusiasm',
			'Motivation',
			'Creative',
			'Imagination',
			'Inspiration',
			'Curiosity',
			'Inquisitive',
			'Daring',
			'Zeal',
			'Ambition',
			'Energetic',
			'Vigorous',
			'Movement',
			'Discovery',
			'Radiance',
			'Beauty',
			'Resilience',
			'Noble',
			'Loyal',
			'Sincere',
			'Integrity',
		],
		// Nature-related words are often used in names, but might be of secondary importance.
		[
			'Sunshine',
			'Summer',
			'Warmth',
			'Rain',
			'Storm',
			'Snow',
			'Cloud',
			'Breeze',
			'Mist',
			'Sunny',
			'Gale',
			'Calm',
			'Dawn',
			'Dusk',
			'Rainbow',
			'Spring',
			'Autumn',
			'Winter',
			'Frost',
			'Harvest',
			'Blossom',
			'Leaf',
			'Woodland',
			'Grass',
			'Gusty',
			'Warm',
			'Chill',
			'Sunbeam',
			'Drizzle',
			'Adventure',
			'Explorer',
			'Energy',
			'Sporty',
			'Thrill',
			'Light',
			'Serenity',
			'Harmony',
			'Prosperity',
			'Fortitude',
		],
	];

	// Now, we flatten the 2D array into a 1D array to get a single list of keywords.
	const categoryTypes = groupedCategoryTypes.reduce((accumulator, value) => accumulator.concat(value), []);


	// let cinemaTypes = [
	// 	{ value: 'tv show', title: 'TV Show' },
	// 	{ value: 'movie', title: 'Movie' },
	// 	{ value: 'tv show or movie', title: 'No Preference' }
	// ];
</script>

<div class="pt-6 md:pt-10 text-slate-200">
	<div>
		<!-- <div class="mb-8">
			<div class="mb-4 font-semibold text-lg">What kind of cinema are you searching for?</div>
			<div class="flex items-center">
				{#each cinemaTypes as type (type.value)}
					<button
						on:click={() => {
							cinemaType = type.value;
						}}
						class={`${
							cinemaType === type.value ? 'bg-cyan-600/40' : ''
						} text-slate-200 font-bold mr-2 text-sm mt-2 py-2 px-4 rounded-full border border-cyan-600`}
					>
						{type.title}
					</button>
				{/each}
			</div>
		</div> -->
		<div>
			<div class="mb-4 font-semibold text-lg">
				Select all keyword that you want the name to represent.
			</div>
			<div class="flex items-center flex-wrap">
				{#each categoryTypes as category}
					<label
						class={`${
							selectedKeywords.includes(category) ? 'bg-cyan-600/40' : ''
						} text-slate-200 font-bold mr-2 mt-2 text-sm py-2 px-4 rounded-full border border-cyan-600`}
					>
						<input
							class="hidden"
							type="checkbox"
							bind:group={selectedKeywords}
							name="categories"
							value={category}
						/>
						{category}
					</label>
				{/each}
			</div>
		</div>
		<div class="mt-8">
			<div class="mb-4 font-semibold text-lg">
				Write any other meanings, keywords, or specifications here. Be as picky as you'd like.
			</div>
			<textarea
				bind:value={specificDescriptors}
				class="bg-white/40 border border-white/0 p-2 rounded-md placeholder:text-slate-800 text-slate-900 w-full h-20 font-medium"
				placeholder="Ex. Must start with a Z."
			/>
			<button
				on:click
				class={`${
					loading
						? 'bg-cyan-400/50'
						: 'bg-cyan-600 hover:bg-gradient-to-r from-cyan-700 via-cyan-600 to-cyan-700 '
				} mt-4 w-full h-10 text-white font-bold p-3 rounded-full flex items-center justify-center`}
			>
				{#if loading}
					<LoadingIndicator />
				{:else}
					<p>Curate My List</p>
				{/if}
			</button>
		</div>
	</div>
</div>
