<script>
	import issuesByCandidate from "./data/issues-by-candidate.js"
	import ideologyByCandidate from "./data/ideology-by-candidate.js"
	import trialWatchByCandidate from "./data/trial-watch-by-candidate.js"
	import partyAffiliationByCandidate from "./data/party-affiliation-by-candidate.js"
	import definitelyByCandidate from "./data/definitely-by-candidate.js"
	import winnerByCandidate from "./data/winner-by-candidate.js"
	import votedByCandidate from "./data/voted-by-candidate.js"
	import votedAllByCandidate from "./data/voted-all-by-candidate.js"
	import changeByCandidate from "./data/change-by-candidate.js"
	import ethnicityByCandidate from "./data/ethnicity-by-candidate.js"
	import ageByCandidate from "./data/age-by-candidate.js"
	import educationByCandidate from "./data/education-by-candidate.js"
	import regionByCandidate from "./data/region-by-candidate.js"
	import modeByCandidate from "./data/mode-by-candidate.js"
	import genderByCandidate from "./data/gender-by-candidate.js"
	import Heatmap from "./Heatmap/Heatmap.svelte"
</script>

<main>
	<h1>
		National Emerson Poll Results
	</h1>

	<p>
		These heatmaps were created using survey data from the <a href="http://emersonpolling.com/2020/01/24/national-2020-biden-and-sanders-battle-in-two-way-race-for-democratic-nomination/">National 2020 Emerson Poll</a>, collected between 1/21 - 1/23, 2020. Keep in mind that only 497 responded to the poll, so take results with a grain of salt!
	</p>
	<p>
		This site was created by <a href="http://twitter.com/wattenberger">Amelia Wattenberger</a>, and the code is up on <a href="https://github.com/Wattenberger/01-2020-emerson-national-poll">Github</a>.
	</p>
	<br />

	<Heatmap
		xLabel="When it comes to deciding for whom you will vote for president, which one of the following is the single most important issue in deciding for whom you will vote?"
		yLabel="Of the following Democratic candidates for President, who would you be most likely to support?"
		data={issuesByCandidate}
	/>
	<Heatmap
		xLabel="Which of the following political ideologies do you most identify as?"
		yLabel="Of the following Democratic candidates for President, who would you be most likely to support?"
		data={ideologyByCandidate}
	/>
	<Heatmap
		xLabel="How much of the live coverage of the Senate impeachment trial will you watch?-- almost all of it, a lot of it, some of it, hardly any of it, or none of it?"
		yLabel="Of the following Democratic candidates for President, who would you be most likely to support?"
		data={trialWatchByCandidate}
	/>
	<Heatmap
		xLabel="What is your party registration?"
		yLabel="Of the following Democratic candidates for President, who would you be most likely to support?"
		data={partyAffiliationByCandidate}
	/>
	<Heatmap
		xLabel="Will you definitely vote for your candidate or is there at least a chance you could change your mind and vote for someone else?"
		yLabel="Of the following Democratic candidates for President, who would you be most likely to support?"
		data={definitelyByCandidate}
	/>
	<Heatmap
		xLabel="Regardless of who you will vote for, who do you think will be the Democratic nominee?"
		yLabel="Of the following Democratic candidates for President, who would you be most likely to support?"
		data={winnerByCandidate}
	/>
	<Heatmap
		xLabel="Who did you vote for in the Democratic Primary in 2016?"
		yLabel="Of the following Democratic candidates for President, who would you be most likely to support?"
		data={votedByCandidate}
	/>
	<Heatmap
		xLabel="Who did you vote for in the 2016 election?"
		yLabel="Of the following Democratic candidates for President, who would you be most likely to support?"
		data={votedAllByCandidate}
	/>
	<Heatmap
		xLabel="If your choice of candidate does not receive the Democratic nomination, will you still vote for the Democratic nominee?"
		yLabel="Of the following Democratic candidates for President, who would you be most likely to support?"
		data={changeByCandidate}
	/>
	<Heatmap
		xLabel="Ethnicity?"
		yLabel="Of the following Democratic candidates for President, who would you be most likely to support?"
		data={ethnicityByCandidate}
	/>
	<Heatmap
		xLabel="What is your age range?"
		yLabel="Of the following Democratic candidates for President, who would you be most likely to support?"
		data={ageByCandidate}
	/>
	<Heatmap
		xLabel="What is the highest level of education you have attained?"
		yLabel="Of the following Democratic candidates for President, who would you be most likely to support?"
		data={educationByCandidate}
	/>
	<Heatmap
		xLabel="Region?"
		yLabel="Of the following Democratic candidates for President, who would you be most likely to support?"
		data={regionByCandidate}
	/>
	<Heatmap
		xLabel="Mode"
		yLabel="Of the following Democratic candidates for President, who would you be most likely to support?"
		data={modeByCandidate}
	/>
	<Heatmap
		xLabel="Gender"
		yLabel="Of the following Democratic candidates for President, who would you be most likely to support?"
		data={genderByCandidate}
	/>
</main>

<style>
	main {
		color: #2C3A47;
		padding: 1em 2em;
		margin: 0 auto;
		width: 900px;
	}

	h1 {
		font-size: 4em;
		font-weight: 100;
	}
</style>