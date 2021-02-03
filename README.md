# WebScraper

NodeJS web scraper using cheerio

## What can you use WebScraper for ?

1. Extract data to your NODE.JS application conveniently.
2. Extract important data from the target web page.

## How do you use WebScraper ?

- Run to install node dependencies.

        npm install

- Change the object array. `var title` and `var json` to the data you want to extract from the website.

- Change the inner functions to trim() and get the objects in to your array. Make sure the customer variable names you use are consistent throught the application.

server.js

```
  request(url, function (error, response, html) {
        if (!error) {
            var $ = cheerio.load(html);

            var title, release, rating;
            var json = { title: "", release: "", rating: "" };

            $('.title_wrapper').filter(function () {
                var data = $(this);
                title = data.children().first().text().trim();
                release = data.children().last().children().last().text().trim();

                json.title = title;
                json.release = release;
            })

            $('.ratingValue').filter(function () {
                var data = $(this);
                rating = data.text().trim();

                json.rating = rating;
            })
        }
```

- Run to start the majic!

        node server.js

- Go to http://localhost:8081/scrape

- The desired scrape will be printed(outputed) in the `output.json` file.
