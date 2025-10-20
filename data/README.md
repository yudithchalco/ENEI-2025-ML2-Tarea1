# Data Descriptions

## Disaster Tweets (`disaster_tweets.csv`)

* `id`: A unique identifier for each tweet
* `text`: The text of the tweet
* `location`: The location the tweet was sent from (may be blank)
* `keyword`: A particular keyword from the tweet (may be blank)
* `target`: Denotes whether a tweet is about a real disaster (1) or not (0)

## Carseats (`ISLP.load_data("Carseats")`)

* `Sales`: Unit sales (in thousands) at each location
* `CompPrice`: Price charged by competitor at each location
* `Income`: Community income level (in thousands of dollars)
* `Advertising`: Local advertising budget for company at each location (in thousands of dollars)
* `Population`: Population size in region (in thousands)
* `Price`: Price company charges for car seats at each site
* `ShelveLoc`: A factor with levels Bad, Good and Medium indicating the quality of the shelving location for the car seats at each site
* `Age`: Average age of the local population
* `Education`: Education level at each location
* `Urban`: A factor with levels No and Yes to indicate whether the store is in an urban or rural location
* `US`: A factor with levels No and Yes to indicate whether the store is in the US or not

