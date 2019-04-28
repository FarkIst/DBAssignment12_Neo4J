# DBAssignment12_Neo4J

In order to run the NEO4J Docker Container we used the following command, as used by Kasper in the Lecture Note 12.

We've also added the flag to our container below in order to load the data. 
```
docker run -d -v $(pwd):/var/lib/neo4j/import --name neo4j --rm --publish=7474:7474 --publish=7687:7687 --env NEO4J_AUTH=neo4j/1234 neo4j
```
## Exercise 1 
Adding mentions-list using the full dataset. 

```
USING PERIODIC COMMIT
LOAD CSV WITH HEADERS FROM "file:///some2016UKgeotweets.csv" AS row 
    FIELDTERMINATOR ";"
    CREATE(tweets:Tweet{id:row["Tweet Id"],
    date:row.Date, 
    hour:row.Hour,
    userName:row["User Name"], nickName:row.Nickname, 
    bio:row.Bio,
    tweetContent:row["Tweet content"], rts:row.RTs, 
    latitude: row.Latitude, longitude: row.Longitude, country: row.Country, place: row["Place (as appears on Bio)"],
    followers: row.Followers, following: row.Following, listed: row.Listed, tweetLanguage: row["Tweet language (ISO 639-1)"], tweetUrl:   row["Tweet Url"]
    })
RETURN row
```
## Exercise 2 
¯\_(ツ)_/¯ Not sure on this solution.

MATCH(t:Tweet{}) SET t.mentions = [];

MATCH(e:Tweet), 
SET e.tweetContent = REPLACE(e.tweetContent, "@ ", "@" ) RETURN e;


## Exercise 3 
The question here seems quite unclear, not sure what kind of result we're being asked for. 
