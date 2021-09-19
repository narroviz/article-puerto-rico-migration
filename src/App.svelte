<script>
  import Header from "./Header.svelte";
  import Intro from "./Intro.svelte";
  import ColumnChart from "./ColumnChart.svelte";
  import Legend from "./Legend.svelte";
  import MapChart from "./MapChart.svelte";

  import acsData from '../public/assets/data/acs_migration_data.js'
  import countyFlows from '../public/assets/data/county_flows.json'
  import { isMobile } from './utils.js'


  console.log(countyFlows)
</script>


<Header/>

<main>
	<div style="height:100%; max-width: 1200px; margin: auto;">
		<Intro/>
		<div class='article'>
			<p>
				Following the <a href="https://www.census.gov/programs-surveys/decennial-census/decade/2020/2020-census-main.html" target='_blank' class="paragraph-link-text">2020 Census</a> data release, many <a href="https://www.nbcnews.com/news/latino/puerto-ricos-population-fell-118-33-million-census-shows-rcna767" target='_blank' class="paragraph-link-text">news</a> <a href="https://www.theweeklyjournal.com/online_features/we-are-fewer-and-we-are-older/article_2aa1e03a-1034-11ec-b488-cb82db0bcc50.html" target='_blank' class="paragraph-link-text">outlets</a> <a href="https://belatina.com/puerto-rico-population-decrease-census/" target='_blank' class="paragraph-link-text">noted</a> that, over the past decade, Puerto Rico lost 11.8% of its population. In the latter part of the decade, natural disasters, governmental instability, and the global pandemic only exacerbated Puerto Rico’s years-long trend of emigration to the U.S.
				<br/><br/>
				Despite this difficult trend, it's worthwhile to understand that during the decade, people have still returned to live in Puerto Rico. And many more in the diaspora want to go back. Even in the years following the devastation of Hurricane María (2017), waves of boricuas had started returning to the island. For many, returning was an "<a href="https://remezcla.com/features/culture/young-diasporicans-decided-repatriate-puerto-rico/" target='_blank' class="paragraph-link-text">effort to preserve culture, reclaim land, serve their communities and imagine a different reality for themselves</a>." They wanted to help rebuild and transform the island.
			</p>
			<h1>Returning to Puerto Rico</h1>
			<p>
				2019 was the most recent year with granular Census data about migration to and from Puerto Rico. In this pre-pandemic world, every age group was starting to return to Puerto Rico in increasing numbers. Leading this return were Puerto Ricans in the 25-34 age group. In 2019, they were moving to the island in larger numbers than any other year over the past decade. The same was true for all age groups over 45, as you can see in the data below.
			</p>
			<p class='small-multiples-title'>Migration to Puerto Rico by Age Group <span class="small-multiples-subtitle">(2010 - 2019)</span></p>
			<Legend
				title="Num. Arrivals to Puerto Rico"
			>
			</Legend>
			<div class="small-multiples-container">
				{#each acsData as { ageGroup, timeSeries }}
					<div>
						<p class='small-multiple-title'>{ageGroup}</p>
						<div class="small-multiple">
							<ColumnChart data="{timeSeries}"/>
						</div>
					</div>
				{/each}
			</div>
			<p class='chart-data-source'><span class="bold">Data: </span><a href="https://data.census.gov/cedsci/table?q=migration&g=0400000US72&tid=ACSST1Y2010.S0701PR&hidePreview=false" target="_blank" class="chart-data-link">American Community Survey 1-Year Estimates</a></p>
			<p>
				In line with global trends toward urbanization, the majority of people settled in the metropolitan area around San Juan. Many returned to Puerto Rico directly from places they had emigrated to after María: places like Orange County, FL (contains Orlando). This migratory "revolving door" is known as <a href="https://en.wikipedia.org/wiki/Circular_migration#Puerto_Rico" target="_blank" class="paragraph-link-text">circular migration</a>, and it has been a central, though difficult, element of the Puerto Rican identity for more than a century of U.S. occupation.
				<br/><br/>
				While most of the recent net migration was toward the U.S., a few prominent U.S. counties, like New York County, NY and Los Angeles County, CA, actually contributed a net migration back to the island. Below, you can <span class="bold">click on the municipios</span> and see yearly estimates of how many people migrated to Puerto Rico, and where they came from.
			</p>
			<p class='small-multiples-title'>Avg. Yearly Arrivals by Municipio <span class="small-multiples-subtitle">(2015 - 2019)</span></p>
			<Legend 
				title="Avg. Yearly Arrivals"
				labels={['0', '800', '1.6K', '2.4K', '3.2K', '4K']}
				legendHeight={isMobile.any() ? 14 : 22}
				legendWidth={isMobile.any() ? 26 : 34}
				continuous={true}
				noData={true}
			>
			</Legend>
			<MapChart/>
			<div class='chart-data-source table-bottom'><span class="bold">Data: </span><a href="https://www.census.gov/data/tables/2019/demo/geographic-mobility/county-to-county-migration-2015-2019.html" target="_blank" class="chart-data-link">U.S. Census County-to-County Migration Flows</a></div>
			<h1>Post-Pandemic</h1>
			<p>
				Since granular Census data lags reality by a couple years, it's unclear how much the pandemic has affected these past trends. COVID-19 has hit <a href="https://centropr.hunter.cuny.edu/research/data-center/data-sheets/small-business-pulse-survey-shows-breadth-covid-19-impact" target="_blank" class="paragraph-link-text">Puerto Rico’s economy</a> very hard, which can have large repercussions on people's livelihoods, opportunities and movements. Hopefully, this has not completely stamped out the short term momentum of people returning to the island.
				<br/><br/>
				There are reasons, however, to be optimistic about the long run. Societally, a renewed focus on respecting heritage is inspiring young and old generations alike to revisit where they’re from. Many are recognizing that "<a href="https://remezcla.com/features/culture/young-diasporicans-decided-repatriate-puerto-rico/" target='_blank' class="paragraph-link-text">that the way of life in the U.S. is not sustainable</a>," from either a consumption or work-life perspective. For many, the pandemic’s effect of isolation has also strengthened the desire to return to Puerto Rico’s distinct community, culture and connection with nature.
				<br/><br/>
				Economically, opportunities may be increasing longer term. As Puerto Rico continues to lead in <a href="https://www.miamiherald.com/news/coronavirus/article253754878.html" target='_blank' class="paragraph-link-text">vaccination rates</a>, effects of the pandemic will wane and small businesses can recover. With the pandemic’s acceleration of remote work, many Puerto Ricans in the diaspora may also gain the flexibility to move back to the island. 
				<br/><br/>
				Additionally, opportunities for Puerto Rican-led entrepreneurship are increasing, with programs like <a href="https://www.bravofamilyfoundation.org/rising-entrepreneurs/" target='_blank' class="paragraph-link-text">Rising Entrepreneurs</a> and <a href="https://www.bravofamilyfoundation.org/community-leaders/" target='_blank' class="paragraph-link-text">Community Leaders</a>, created by the Bravo Family Foundation. The push to build a distinctly Puerto Rican economy outside of the <a href="https://www.cnbc.com/2017/09/26/heres-how-an-obscure-tax-change-sank-puerto-ricos-economy.html" target='_blank' class="paragraph-link-text">whims</a> or <a href="https://www.npr.org/sections/thesalt/2017/05/13/527934047/how-puerto-rico-lost-its-home-grown-food-but-might-find-it-again" target='_blank' class="paragraph-link-text">abuses</a> of <a href="https://www.cato.org/blog/new-reports-detail-jones-acts-cost-puerto-rico" target='_blank' class="paragraph-link-text">U.S. legislation</a> can ideally lead to a stronger long-term economy.
				<br/><br/>
				For people hoping to return to la Isla del Encanto, they will find myriad intiatives on the island working to improve lives. While there are many issues to work through and solve in Puerto Rico, there remains plenty of evidence for a hopeful future.
	        </p>
		</div>

	</div>
</main>

<style>
	.bold {
		font-weight: 500;
	}

	.table-bottom {
		max-width: 600px;
		border-top:  1px solid black;
	}

	.chart-data-link {
		font-weight: 200;
		color: #aaa;
	}

	.chart-data-link:hover {
		cursor: pointer;
		text-decoration: none; 
		color: #04A933;
		font-weight: 200;
		border-bottom: 1px solid #04A933;
	}

	.chart-data-source {
		width: 100%;
		font-size: 13px;
		font-family: 'Avenir';
		text-align: center;
		font-weight: 200;
		color: #aaa;
		margin: 0 auto;
		padding-top: 30px;
	}



	.small-multiples-container {
		max-width: 800px;
		margin: auto;
		display: grid;
		grid-template-areas: 'a a a a';
		width: 100%;
		column-gap: 20px;
		row-gap: 20px;
	}

	.small-multiple {
		width: 150px;
		height: 120px;
		margin: auto;
	}

	.small-multiples-title, .small-multiples-subtitle {
		width: 100%;
		font-size: 30px;
		font-family: 'Avenir';
		text-align: center;
		font-weight: 500;
		margin: 0 auto;
		padding-bottom: 20px;
	}

	.small-multiples-subtitle {
		font-size: 24px;
	}

	.small-multiple-title {
		width: 100%;
		font-size: 20px;
		font-family: 'Avenir';
		text-align: center;
		margin: 0 auto;
	}

	@media (max-width: 600px) {
		.small-multiples-container {
			grid-template-areas: 'a a';
			column-gap: 20px;
			row-gap: 30px;
		}
		.small-multiple {
			width: 125px;
			height: 100px;
		}
		.small-multiples-title {
			font-size: 20px;
			line-height: 1;
			padding-bottom: 10px;
		}
		.small-multiples-subtitle {
			font-size: 14px;
		}
		.small-multiple-title {
			font-size: 18px;
		}
		.chart-data-source {
			padding-top: 10px;
			font-size: 11px;
		}
	}


	.paragraph-link-text {
		font-weight: 200;
		border-bottom: 1px solid black;
		color: black;
	}

	.paragraph-link-text:hover {
		cursor: pointer;
		text-decoration: none; 
		color: #04A933;
		font-weight: 200;
		border-bottom: 2px solid #04A933;
	}

	.article {
	    font-family: "Avenir";
	    text-align: left;
	    padding-left: 1rem;
		  padding-right: 1rem;
		  padding-top: 1rem;
	}

	/*
	********************
	       Raleway
	********************
	*/

	@font-face {
	    font-family: 'Raleway';
	    src: url('/assets/fonts/raleway/Raleway-extralight.woff');
	    font-weight: 200;
	    font-style: normal;
	    font-stretch: normal;
	    font-display: swap;
	}

	@font-face {
	    font-family: 'Raleway';
	    src: url('/assets/fonts/raleway/Raleway-medium.woff');
	    font-weight: 400;
	    font-style: normal;
	    font-stretch: normal;
	    font-display: swap;
	}

	@font-face {
	    font-family: 'Raleway';
	    src: url('/assets/fonts/raleway/Raleway-heavy.woff');
	    font-weight: 700;
	    font-style: normal;
	    font-stretch: normal;
	    font-display: swap;
	}

	/*
	********************
	       Avenir
	********************
	*/

	@font-face {
	    font-family: 'Avenir';
	    src: url('/assets/fonts/avenir/Avenir-Light.woff');
	    font-weight: 400;
	    font-style: normal;
	    font-stretch: normal;
	    font-display: swap;
	}

	@font-face {
	    font-family: 'Avenir';
	    src: url('/assets/fonts/avenir/Avenir-Medium.woff');
	    font-weight: 500;
	    font-style: normal;
	    font-stretch: normal;
	    font-display: swap;
	}

	@font-face {
	    font-family: 'Avenir';
	    src: url('/assets/fonts/avenir/Avenir-Heavy.woff');
	    font-weight: 700;
	    font-style: normal;
	    font-stretch: normal;
	    font-display: swap;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}


</style>