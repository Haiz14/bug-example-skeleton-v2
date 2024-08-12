<script lang="ts">
	type IssuesData = {
		exampleURL: string;
		codeSrcURL: string;
	};
	const baseUrl = "https://github.com/haiz14/basic-examples/blob/main/src/routes";

	function getIssueData(exampleUrl: string): IssuesData {
		return {
			exampleURL: "/" + exampleUrl,
			codeSrcURL: `${baseUrl}/${exampleUrl}/+page.svelte`,
		};
	}

	const issues: Record<string, IssuesData> = {
		" input group grid breaks on pressing enter during focus in mobile": getIssueData("/focus-breaks-grid-column"),
		"firefox android mobile, input group broken": getIssueData("/firefox-input-group-broken"),
		"input group grid-row, focus does not work oroperly on mobile": getIssueData("/focus-breaks-grid-row"),
		};

</script>

<main class="text-center my-12 md:my-16 mx-2 md:mx-4">
	<h1 class="h1 mb-6 md:mb-8">Issues</h1>
	<div class="flex flex-col gap-4 md:gap-6 items-center"> 
		{#each Object.entries(issues) as [issue, { exampleURL, codeSrcURL }]}
			<div class="card p-3 md:p-5 md:max-w-[50%] md:min-w-[50%]">
				<p class="text-lg md:text-xl pb-3">{issue}</p>
				<div class="flex gap-3 md:gap-5 justify-center">
					<a class="chip variant-ghost-primary" href={codeSrcURL}>code-src</a>
					<a class="chip variant-ghost-secondary" href={exampleURL}>live-example</a>
				</div>
			</div>
		{/each}
	</div>
</main>
