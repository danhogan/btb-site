---
title: Scraping ESPN Fantasy Baseball Data with Node.js
date: 2016-06-30 12:00:00
excerpt: Summer is just about here and baseball is back in full swing
type: post
blog: true
tags:
    - Tech
---

I already wrote [about the UI part of this](using-d3-js-to-analyze-fantasy-baseball-data/). This is about how I gathered the data to begin with.

Ideas for this little project began when looking at the record board in my fantasy baseball league. We keep yearly, weekly, and even daily records. Often times a daily or weekly record can be missed. Instead of clicking through the day by day views and arduously comparing all the numbers, I figured there must be an easier way. ESPN thinks they’re too cool for a public API, so I decided I would make a little something to grab the data myself. I just wanted to organize the data I could already see. Simple as that.

With these things in mind, I knew a trip to the Node abode was in store. I quickly found a nice little package called [Cheerio](https://github.com/cheeriojs/cheerio)  to give me jQuery-like powers. I was then able to scan through the tables to store the stats in my own JavaScript object via a slightly-larger-than-I-like-but-I-don’t-know-how-to-do-it-smarter case statement.

```javascript
function processHTML(html, thisCallback){
	var $ = cheerio.load(html);
		    	
	var x = 0;
	var weekStats = [];
	
	$('.linescoreTeamRow td').each(function(i, element){
  		var line = $(this).text();

  		if(i % 15 == 0){
  			if(i > 0){
  				x++;
  			}

  			weekStats[x] = {};
		}
  		
  		var z = x*15
  		
  		switch(i){
	      	case 0 + z:
	      		weekStats[x].Name = line;
	      		break;
	      	case 2 + z:
	      		weekStats[x].R = line;
	      		break;
	      	case 3 + z:
	      		weekStats[x].HR = line;
	      		break;
	      	case 4 + z:
	      		weekStats[x].RBI = line;
	      		break;
	      	case 5 + z:
	      		weekStats[x].SB = line;
	      		break;
	      	case 6 + z:
	      		weekStats[x].AVG = line;
	      		break;
	      	case 8 + z:
	      		weekStats[x].K = line;
	      		break;
	      	case 9 + z:
	      		weekStats[x].W = line;
	      		break;
	      	case 10 + z:
	      		weekStats[x].SV = line;
	      		break;
	      	case 11 + z:
	      		weekStats[x].ERA = line;
	      		break;
	      	case 12 + z:
	      		weekStats[x].WHIP = line;
	      		break;
	      	case 14 + z:
	      		weekStats[x].Record = line;
	      		break;

	      	default:
	      		break;
		}
	});

	thisCallback(weekStats);
}
```

My favorite part of this little project was combining this scraper with the [async](https://github.com/caolan/async) package. It felt pretty cool to asynchronously grab the data from every week with `async.map`. (If you run the program yourself it’ll console log when each week is processed).

```javascript
async.map(weekArray, function(weekNumber, callback){
	request('http://games.espn.go.com/flb/scoreboard?leagueId=' + leagueId + '&seasonId=' + seasonYear + '&matchupPeriodId=' + weekNumber, function (error, response, html) {
		if (!error && response.statusCode == 200) {
			processHTML(html, function(data){
				console.log("finished week number " + weekNumber);
				callback(null, data);
			});
		} else {
			console.log(response);
			console.log(error);
		}
	});
}, function(err, season){
	if(err){
		console.log(err);
	} else {
		callbackToMain(season);
	}
});
```

There may be many things that make my fantasy baseball league different from yours, but it was fairly close to standard the past three years. There are still many changes to be made to make this scraper more “universal.” You can run it yourself and explore the rest with the [code on Github](https://github.com/danhogan/fantasy-baseball-scrape). I hope to make a client-side-only version with artoo.js so it can easily be hosted and used on Github pages.