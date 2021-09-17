<script>
	import { ARTICLE_TITLE, ARTICLE_TITLE_DATE, ARTICLE_DESCRIPTION } from '../config.mjs'
</script>

<div class='intro'>
	<h1 class='intro__hed'>{ARTICLE_TITLE}</h1>
	<p class='intro__dek'>{ARTICLE_DESCRIPTION}</p>
	<p class='intro__byline'>By
		<a href='http://dnewcomb.com' class="link-text" target='_blank'>
			<strong>David Newcomb<strong>
		</a>
	</p>
	<time class='intro__time'>{ARTICLE_TITLE_DATE}</time>
	<div class='intro__prelude'>
		<p>
			As many <a href="https://www.nbcnews.com/news/latino/puerto-ricos-population-fell-118-33-million-census-shows-rcna767" target='_blank' class="paragraph-link-text">news</a> <a href="https://www.theweeklyjournal.com/online_features/we-are-fewer-and-we-are-older/article_2aa1e03a-1034-11ec-b488-cb82db0bcc50.html" target='_blank' class="paragraph-link-text">outlets</a> <a href="https://belatina.com/puerto-rico-population-decrease-census/" target='_blank' class="paragraph-link-text">noted</a> following the <a href="https://www.census.gov/programs-surveys/decennial-census/decade/2020/2020-census-main.html" target='_blank' class="paragraph-link-text">2020 Census'</a> initial data release, over the past decade, Puerto Rico’s population dwindled by 11.8%. In the latter part of the decade, natural disasters, governmental instability, and the global pandemic only exacerbated Puerto Rico’s years-long trend of emigration to the U.S.
			<br/><br/>
			Despite this difficult trend, it's worthwhile to understand that during this decade, people have still returned to live in Puerto Rico and many more in the diaspora want to go back. For instance, in the years following the devastation of Hurricane María (2017), waves of boricuas had started returning to the island. For many, returning was an "<a href="https://remezcla.com/features/culture/young-diasporicans-decided-repatriate-puerto-rico/" target='_blank' class="paragraph-link-text">effort to preserve culture, reclaim land, serve their communities and imagine a different reality for themselves</a>." They wanted to help rebuild and transform the island.
		</p>
		<h1>Returning to Puerto Rico</h1>
		<p>
			2019 was the most recent year with granular Census data about migration to and from Puerto Rico. In this pre-pandemic world, every age group was starting to return to Puerto Rico in increasing numbers. Leading this return were Puerto Ricans in the 25-34 age group. In 2019, they were moving to the island in larger numbers than any other year over the past decade. The same was true for all age groups over 45, as you can see in the data below.
			<br/><br/>
			In line with global trends toward urbanization, the majority of people settled in the metropolitan area around San Juan. Many also returned to Puerto Rico directly from places they had emigrated to immediately after María: places like Maricopa County, FL (contains Orlando). This migratory revolving door is known as circular migration, and it has been a central, and difficult, element of the Puerto Rican identity throughout decades of U.S. occupation.
			<br/><br/>
			A few prominent counties, like X and Y, even experienced a net migration back to the island. Below, you can click around Puerto Rico's municipios and see where people had returned from, both within the U.S. and worldwide.
		</p>
		<h1>Post-Pandemic</h1>
		<p>
			Since granular Census data lags reality by a couple years, it's unclear how much the pandemic has affected these past trends. COVID-19 has hit <a href="https://centropr.hunter.cuny.edu/research/data-center/data-sheets/small-business-pulse-survey-shows-breadth-covid-19-impact" target="_blank" class="paragraph-link-text">Puerto Rico’s economy</a> very hard, which can have large repercussions on people's livelihoods, opportunities and movements. Hopefully, this has not completely stamped out any short term momentum of people returning to the island.
			<br/><br/>
			There are reasons, however, to be optimistic about the long run. Societally, a renewed focus on respecting heritage is inspiring young and old generations alike to revisit where they’re from. Many are recognizing that "<a href="https://remezcla.com/features/culture/young-diasporicans-decided-repatriate-puerto-rico/" target='_blank' class="paragraph-link-text">that the way of life in the U.S. is not sustainable</a>" from either a consumption or work perspective. For many, the pandemic’s effect of isolation has also strengthened the desire to return to Puerto Rico’s distinct community, culture and connection with nature.
			<br/><br/>
			Economically, some opportunities may be increasing longer term. As Puerto Rico continues to lead in <a href="https://www.miamiherald.com/news/coronavirus/article253754878.html" target='_blank' class="paragraph-link-text">vaccination rates</a>, effects of the pandemic will wane and small businesses can start recovering. With the pandemic’s acceleration of remote work, many Puerto Ricans in the diaspora may also gain the flexibility to move back to the island. 
			<br/><br/>
			Additionally, opportunities for Puerto Rican-led entrepreneurship are increasing, with programs like <a href="https://www.bravofamilyfoundation.org/rising-entrepreneurs/" target='_blank' class="paragraph-link-text">Rising Entrepreneurs</a> and <a href="https://www.bravofamilyfoundation.org/community-leaders/" target='_blank' class="paragraph-link-text">Community Leaders</a>, created by the Bravo Family Foundation. The push to build a distinctly Puerto Rican economy outside of the whims or abuses of U.S. legislation can ideally lead to a stronger long-term economy.
			<br/><br/>
			For people hoping to return to la Isla del Encanto, they will find myriad intiatives on the island working to improve lives. While there are many issues to work through and solve in Puerto Rico, there remains plenty of evidence for a hopeful future.
        </p>
	</div>
</div>

<style>
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

	.link-text {
		font-weight: 500;
		border-bottom: 1px solid black;
		color: black;
	}

	.link-text:hover {
		cursor: pointer;
		text-decoration: none; 
		color: #04A933;
		font-weight: 700;
		border-bottom: 2px solid #04A933;
	}
	.intro {
	  margin: 0 auto;
	  padding-left: 1rem;
	  padding-right: 1rem;
	  padding-top: 1rem;
	  max-width: calc(1000px - 2rem);
	}
	.intro__hed {
	  max-width: 60rem;
	  font-weight: 200 !important;
	  font-size: 32px;
	  margin: 0 auto;
	  line-height: 1.4;
	  text-align: center;
	}
	.intro__dek {
	  max-width: 40rem;
	  margin: 0 auto;
	  margin-top: 1rem;
	  font-weight: 200 !important;
	  font-size:  18px;
	  line-height: 1.65;
	  text-align: center;
	}
	.intro__byline {
		font-family: 'Avenir';
	  max-width: 40rem;
	  margin: 0 auto;
	  margin-top: 1rem;
	  font-size:  18px;
	  line-height: 1.65;
	  text-align: center;
	}
	.intro__time {
	  display: block;
	  max-width: 40rem;
	  font-weight: 200 !important;
	  font-size: 18px;
	  margin: 0 auto;
	  margin-top: 1rem;
	  text-align: center;
	}
	.intro__prelude {
	    font-family: "Avenir";
	    text-align: left;
	}
</style>