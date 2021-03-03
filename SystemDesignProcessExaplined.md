_**The examples consider design twitter as a question.**_

## Step 1 - Requirement Clarification

* Need to iddentify the scope of the problem. 

Ex - few questions to ask for scoping: 
     1. Users of service post tweets, like them, save them
     2. Tweets will contains photos and videos ?
     3. Will we need to search for a tweet ?
     4. Do we need to ddesign notification for new tweets ?


## Step 2 - Back-of-envolope Estimation

* Try to estimate the scale of the system
* Focus on asking questions like below: 
  1. Scaling 
  2. Sharding/Partitioning 
  3. Load Balancing 
  4. Caching 
  5. Network bandwidth

Ex - What scale is expected for the app( no of tweets, tweet views, shares, timelines generation per sec)


## Step 3 - System Design Interface

* Try to define the API contacts.

Ex - postTweet(user_id, tweet_data, tweet_location, user_location, timestamp)


## Step 4 - Defining data model

* Try to iddentify the entities involved.
* Figure out relationships between them i.e. interactions
* Data Management - store, transport, encrypt etc

Ex - User - UserId, Email, DOB, Name, Creation Date, LastLogin

## Step 5 - High Level Design

* Create a block diagram depicting the core components and the data flow.
* This will give end to end idea of the service created.

Ex - For Twitter, at a high-level, we will need multiple application servers to serve all the read/write requests with load balancers in front of them for traffic distributions. If we’re assuming that we will have a lot more read traffic (compared to write), we can decide to have separate servers to handle these scenarios. On the back-end, we need an efficient database that can store all the tweets and support a huge number of reads. We will also need a distributed file storage system for storing photos and videos.


## Step 6 - Detailed Design

* This step is a followup to the previous step.
* Listen to interviewer and look for hints as to what components you will need to dig deep in.
* Present approaches, list out comparisons and tradeoffs.

Ex - Since we will be storing a massive amount of data, how should we partition our data to distribute it to multiple databases? Should we try to store all the data of a user on the same database? What issue could it cause?

## Step 7 - Iddentifying and Resolving Bottlenecks

* Discuss bottlenecks and ways to mitigate them in this.
* To find bottlenecks looks for: 
  1. Single Point of failure 
  2. Server Crash Failovers strategy 
  3. Service Crash Fail over strategy 
  4. Service montitoring and logging

Ex - Do we have enough replicas of the data so that we can still serve our users if we lose a few servers ?
