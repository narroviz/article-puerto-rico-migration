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
</div>

<style>
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
</style>