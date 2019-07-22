#

- Building a `Flask` application that scrapes the ATP website for ranking information and information on players in general (such as win/loss stats) using `BeautifulSoup4`.
- Since ATP ranking data only updates at most every day, I cache the result on the queries in a cache that expires at the start of every day.
- Implemented `docker-compose` to define a microservice for the API as well as a service used to host a test `react` app (docs).
- Implemented `unittest` and `postman` tests to validate the output from the API.
- See: <a href="https://github.com/Sammyalhashe/ATPScraper">https://github.com/Sammyalhashe/ATPScraper</a>  
