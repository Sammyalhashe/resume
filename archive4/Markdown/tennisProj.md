# 

* Writing a webapp (still in development) that webscrapes the ranking history of tennis players Roger Federer, Rafael Nadal, Novak Djokovic, Andy Murray, and Nick Kyrgios.
* The ranking data is displayed on a chart vs. year they played.
* Front end is written in react. Main class components are:
    - Top level app component that passes the chosen player's name down.
    - Body component that calls the backend webscraper, passing the result down.
    - Graph component that recieves the result of the webscraper and plots the data using [<code>chartist.js</code>](https://gionkunz.github.io/chartist-js/).
* Backend webscraper is an <code>express</code> server that uses [<code>cheerio.js</code>](https://github.com/cheeriojs/cheerio) wrapped in a [request-promise](https://github.com/request/request-promise).
    - <code>Cheerio.js</code> scrapes the player's ranking page by element selector.
