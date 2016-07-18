# Google Custom Search

Adding search to your website, provided by Google's [Custom Search Engine](https://cse.google.com/cse/), adds a powerful dimension to your website. [Solodev](https://www.solodev.com/) takes it a step further with some professional styling, making your search bar/page looks as good as the results it delivers while maintaining a fully responsive nature.


## Tutorial

For detailed instructions implementing this search bar, view Solodev's [Adding Google Custom Search to your Website](https://www.solodev.com/blog/web-design/code-examples/2014392-adding-google-custom-search-to-your-website.stml) article.

## Demo

Check out a working example on [JSFiddle](https://jsfiddle.net/solodev/2hcbheh8/).

## HTML

The basic HTML markup for the search form is as follows:
```
<form id="searchForm" action="">
			<div class="row">
				<div class="col-md-10 col-sm-12">
					<input id="txtSearchTerm" name="q" class="search-page-search" placeholder="What are you looking for?" value="">
				</div>
				<div class="col-md-2 col-sm-12">
					<input type="submit" class="search-page-search-submit" value="Search">
				</div>
			</div>
		</form>
		<div id="searchResult"></div>
		<div id="output"></div>
		<div class="pager_controls">
			<p>
				<a onclick="documentTrack('#');" href="#" id="lnkPrev" title="Display previous result page" style="display:none;">Previous</a> <a onclick="documentTrack('#');" href="#" id="lnkNext" title="Display next result page" style="display:none;">Next</a>
			</p>
		</div>
```

Additionally, the entire section is wrapped in a simple Bootstrap grid:
```
<div class="container">
	<div class="col-md-12 ct-content">
```

## CSS

All CSS is included in google-search.css. Changing the color scheme is as simple as chaning the "background-color" properties.

## JavaScript

The search relies on a cse key and an optional API key you receive after registering with Google:
```
<!-- Number of searches per day will be limited unless google_api_key is specified (https://console.developers.google.com) -->
<!-- Add your google_cse_id after registering (https://cse.google.com/) -->
<script type="text/javascript">
	<!-- var mGoogleApiKey = "YYYYYYYYY__YYYYYYYYYYY-1111111111111111"; -->
	var mGoogleCustomSearchKey = "123456789123456789123:abcdefghijk";
</script> 
```

Additional processing is included in "search-script.js".

Some simple JavaScript is used to capture the search query and show it in the search bar after results have been loaded:
```
$(document).ready(function(){
	var url = window.location.href; // or window.location.href for current url
	var captured = /q=([^&]+)/.exec(url)[1]; // Value is in [1] ('384' in our case)
	var result = captured ? captured : 'myDefaultValue';
			
	document.getElementById("txtSearchTerm").value = result;
});
```

## External Includes

The slider includes the following third-party resources:
```
<link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" rel="stylesheet" type="text/css"/>
	
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js" type="text/javascript"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/js/bootstrap.min.js" type="text/javascript"></script>
```